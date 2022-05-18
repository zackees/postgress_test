# vids-db

File based database to store video information.

This database provides efficient searches for a variaty of differerent common search patterns, like all videos in a channel, or all videos for everyone in the last 4 hours.

For a front end to this database, please see `vids-db-server`

## Platform Unit Tests

[![Actions Status](https://github.com/zackees/vids-db/workflows/MacOS_Tests/badge.svg)](https://github.com/zackees/vids-db/actions/workflows/test_macos.yml)
[![Actions Status](https://github.com/zackees/vids-db/workflows/Win_Tests/badge.svg)](https://github.com/zackees/vids-db/actions/workflows/test_win.yml)
[![Actions Status](https://github.com/zackees/vids-db/workflows/Ubuntu_Tests/badge.svg)](https://github.com/zackees/vids-db/actions/workflows/test_ubuntu.yml)
[![Actions Status](https://github.com/zackees/vids-db/workflows/Pypi_Publish/badge.svg)](https://github.com/zackees/vids-db/actions/workflows/pypi-publish.yml)


# Api

```
from vids_db import Database, Video
db = vids_db.Database("path/to/database")
vid = Video(...)
db.update(vid)
vids = db.get_video_list(date_start=date_start, date_end=date_end)
print(vids)
```

# Full Tests + linting

  * `git clone https://github.com/zackees/vids-db`
  * `cd vids_db`
  * `tox`

# Networking Requests

  * Please see `Video.parse_json(...)` for generating a type safe input json that can
    be used to insert videos into the database. See also vids-db-server.

# Version

  * 1.2.0: Fixes index. Old databases are abandonded after this update.
  * 1.1.6: Adds migration on startup to fix niave datestamps.
  * 1.1.5: Timezone niave datestamps are now rejected
  * 1.1.4: bulk get_by_url
  * 1.1.3: Adds remove by channel name, to allow deletion
  * 1.1.1: Implements get_channel_names() to find all distinct channel names
  * 1.1.0: vids-db now has full text search disabled by default (too processor intensive)
  * 1.0.9: parse_json now can take in a dict
  * 1.0.8: Adds parse_json
  * 1.0.7: Relaxes views
  * 1.0.6: Relaxes channel name to allow "NTD"
  * 1.0.5: Fixes issue where datestamp was too strict