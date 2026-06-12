---
title: "Deluge"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Zone17 on 2007-10-25
I upgraded to the new Deluge 5.6 (from 5.2) and now it will not open.

This is the terminal output. 

> no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Loading module SpeedLimiter
Initialising plugin SpeedLimiter
Loading module Locations
Initialising plugin Locations
Loading module BlocklistImport
Initialising plugin BlocklistImport
Loading module TorrentPeers
Initialising plugin TorrentPeers
Loading module ExtraStats
Initialising plugin ExtraStats
Loading module NetworkGraph
Initialising plugin NetworkGraph
Loading module ExamplePlugin
Initialising plugin ExamplePlugin
Loading module TorrentNotification
Initialising plugin TorrentNotification
Loading module DesiredRatio
Initialising plugin DesiredRatio
Loading module TorrentPieces
Initialising plugin TorrentPieces
Loading module NetworkHealth
Initialising plugin NetworkHealth
Loading module TorrentCreator
Initialising plugin TorrentCreator
Loading module TorrentSearch
Initialising plugin TorrentSearch
Loading module TorrentFiles
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/usr/lib/python2.5/site-packages/deluge/interface.py", line 65, in __init__
    self.plugins.scan_for_plugins()
  File "/usr/lib/python2.5/site-packages/deluge/plugins.py", line 60, in scan_for_plugins
    mod = __import__(modname, globals(), locals(), [''])
  File "/usr/share/deluge/plugins/TorrentFiles/__init__.py", line 38, in <module>
    from TorrentFiles.tab_files import FilesTabManager
  File "/usr/share/deluge/plugins/TorrentFiles/tab_files.py", line 6, in <module>
    from deluge.files import FilesBaseManager
ImportError: No module named files


---

### Post by Maestro23 on 2007-10-25
How did you upgrade?  I see Deluge 5.4 is the latest in the Ubnuntu Repo's.  If you got the latest package from tthe Deluge website, did you uniinstall the Ubuntu version 1st?

---

### Post by Zone17 on 2007-10-26
> **Maestro23 said:**
> How did you upgrade?  I see Deluge 5.4 is the latest in the Ubnuntu Repo's.  If you got the latest package from tthe Deluge website, did you uniinstall the Ubuntu version 1st?
I downloaded the upgrade from the Deluge website. When that didn&#8217;t work I removed the application and downloaded the supported version from the repositories. Now when I click on it, the program acts like it is going to open and then just doesn&#8217;t.

---

### Post by Zone17 on 2007-10-26
anyone?

---

### Post by lanchongzi on 2007-10-27
same here...
still searching  :-(

---

### Post by wolfvorkian1 on 2007-10-27
I had that problem a few months ago and as I recall how I finally fixed it was to get rid of as much of deluge as I could with the autoremove and purge command and then using locate, I went through and individually deleted any file that had the string deluge in it. Something like this iirc..

```
sudo apt-get autoremove deluge --purge
```

then:

```
sudo updatedb
```

```
locate deluge
```

Then used a file browser as root naturally to delete the files that showed up in the terminal with the string deluge in them and then reinstalled the program. Then it worked okay but not until I had done the above.

---

