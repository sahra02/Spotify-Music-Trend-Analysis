# What Generative AI Was Used For

Throughout this project from time to time Generative AI was used to help in certain situations, where no amount of critical
thinking, pondering or the consumption of thinking biscuits could provide an answer.

This document highlights the areas where Generative AI was used and what it was used for, by providing a "before" and "after" showing what the issue was and what Generative AI propsed, or the original code and the suggested replacement.

Most common use is with CoPilot in VS Code, particularly for changing code when I rename variables, not too reliant on
the code suggestions as they don't always work and sometimes it will happily suggest properties that do not exist!
If it suggests something that is accurate in the current code flow will select it such as creating new columns in a DataFrame  
and it suggests the next line of code. Usually that works fine.

**Scenario One:**

Been developing an ETL library and wanted to use it in this project, however have no idea how to
do it, so asked chatGPT for a solution with this question:

Am using jupyter notebook for a project and the notebook is in a subfolder. However I wish to
use some libraries in a another folder in the same project how can I import them?

I attempted using:

import modGlobal
import modETL_Library as modETL

It replied with a lot of code examples but the most important part was this:

_import sys_
_from pathlib import Path_

_project_root = Path.cwd().parent_
_if str(project_root / "assets" / "python_files") not in sys.path:_
_sys.path.insert(0, str(project_root / "assets" / "python_files"))_

_import modGlobal_  
_import modETL_Library as modETL_

This works so used it everwhere!

**Scenatio Two**

Attempting to get bottom 20 songs into a sunburst plot got strange ZeroDivison error

Asked chatGPT:


chatGpt responded with changing ines of code to:

dfSpotify_DataSet_Temp["count"] = 1

_fig = px.sunburst(dfSpotify_DataSet_Temp.head(20), path=["artists", "album_name", "track_name"], values="count",_ _color="popularity", color_continuous_scale='Viridis', title='Bottom 20 Songs by Popularity Sunburst Plot')_

Which fixed the issue


