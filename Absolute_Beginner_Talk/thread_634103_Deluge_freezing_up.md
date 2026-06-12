---
title: "Deluge freezing up"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Nevon on 2007-12-07
Deluge is my all-time favorite torrent program, but now for some reason it just freezes up whenever I start it.
I've got two downloads running, and it usually says "queing" and then it freezes up. If I don't do anything, one of the downloads might get to "connecting" before freezing up. I don't get any error message if I run it from the terminal either. All I get is this:
> nevon@lolcat:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to -1 bytes per second
Capping upload to -1 bytes per second
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin TorrentSearch
Initialising plugin TorrentFiles
Initialising plugin SpeedLimiter
Initialising plugin ExtraStats
Initialising plugin TorrentNotification
Initialising plugin Locations
Initialising plugin EventLogging
Initialising plugin BlocklistImport
Initialising plugin TorrentPeers
Initialising plugin SimpleRSS
Initialising plugin DesiredRatio
Initialising plugin TorrentPieces
Initialising plugin TorrentCreator
Initialising plugin NetworkGraph
Initialising plugin NetworkHealth
Applying preferences
Starting DHT...
Capping download to -1 bytes per second
Capping upload to -1 bytes per second
Showing window
KilledNote that it doesn't say "killed" until I've "forced exit'd" the program. Is there anyway to fix this without having to start over on the downloads, or should I just reinstall Deluge?

---

### Post by wolfen69 on 2007-12-07
as they fix bugs quite frequently, i would re-install with the latest version [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

---

### Post by hyper_ch on 2007-12-07
you could switch to rtorrent ;)
you should also be able to "copy" the currently downloaded stuff to rtorrent.

---

### Post by Nevon on 2007-12-07
> **hyper_ch said:**
> you could switch to rtorrent ;)
you should also be able to "copy" the currently downloaded stuff to rtorrent.

rtorrent is CLI based, is it not? I feel more comfortable in a GUI, I'm afraid. 
However, I just installed the latest version of Deluge directly from the website, and now it works again!

---

