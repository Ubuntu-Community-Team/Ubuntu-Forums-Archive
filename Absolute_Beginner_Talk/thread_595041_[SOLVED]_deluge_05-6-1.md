---
title: "[SOLVED] deluge 05-6-1"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by haggus on 2007-10-28
I just  tried to use the latest deb file for this program and it stopped working so I uninstalled it using add remove programs and reinstalled it using synaptic. It all works fine now . Anyway running an Athlon 2400 1Gb ram using kernel 2.6.22.6 compiled using the master thread kernel on an updated Ubuntu 7.04 to 7.10. I'm not sure if this is the proper place for this kind of post but I'm curious if anyone else has had problems?

---

### Post by Cochise on 2007-10-28
theres a few more threads around similar, its mostly you have to remove the old version first most people dont they just overwrite with the new one

---

### Post by ThrobbingBrain66 on 2007-10-28
You're going to have to be a bit more specific than "just stopped working".  It may be a packaging problem.

You may want to contact the devs on their IRC channel and/or file a bug:
[http://dev.deluge-torrent.org/](http://dev.deluge-torrent.org/)

---

### Post by haggus on 2007-10-28
Yes I would have to say I ran the deb package before uninstalling the older version I guess I should have read a little further first anyway. I go to open deluge and the gui opens for a second then shuts down. I uninstalled the new deb and installed the package from the repos. It opens up but it doesn't allow any downloads or add torrent files basically just a window. I'm not sure why it does this?

---

### Post by ThrobbingBrain66 on 2007-10-28
First, open Deluge using the terminal to see if it spits out any errors (and post them here).

Also, try renaming the settings folder so that it recreates when you open Deluge (It's located in ~/.config/).

---

### Post by haggus on 2007-10-28
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to -1 bytes per second
Capping upload to 9216 bytes per second
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin BlocklistImport
Initialising plugin SimpleRSS
Initialising plugin ExtraStats
Initialising plugin NetworkHealth
Initialising plugin SpeedLimiter
Initialising plugin TorrentFiles
Initialising plugin TorrentCreator
Initialising plugin TorrentSearch
Initialising plugin TorrentPieces
Initialising plugin NetworkGraph
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin TorrentNotification
Initialising plugin Locations
Initialising plugin DesiredRatio
Applying preferences
Starting DHT...
Capping download to -1 bytes per second
Capping upload to 9216 bytes per second
Showing window
Loading TorrentPeers plugin...
Loading TorrentPieces plugin...
Loading TorrentFiles plugin...
Loading TorrentNotification plugin...
BONG!
It starts up fine but I still can't add delete torrents trying to find the /.config but I have no luck the deluge folder is in /usr/share/deluge

thanks for the help

---

### Post by Maestro23 on 2007-10-28
> **haggus said:**
> Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to -1 bytes per second
Capping upload to 9216 bytes per second
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin BlocklistImport
Initialising plugin SimpleRSS
Initialising plugin ExtraStats
Initialising plugin NetworkHealth
Initialising plugin SpeedLimiter
Initialising plugin TorrentFiles
Initialising plugin TorrentCreator
Initialising plugin TorrentSearch
Initialising plugin TorrentPieces
Initialising plugin NetworkGraph
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin TorrentNotification
Initialising plugin Locations
Initialising plugin DesiredRatio
Applying preferences
Starting DHT...
Capping download to -1 bytes per second
Capping upload to 9216 bytes per second
Showing window
Loading TorrentPeers plugin...
Loading TorrentPieces plugin...
Loading TorrentFiles plugin...
Loading TorrentNotification plugin...
BONG!
It starts up fine but I still can't add delete torrents trying to find the /.config but I have no luck the deluge folder is in /usr/share/deluge

thanks for the help

Goto your home directory: cd /home/username

Then list the contents: ls -a (shows hidden files/directories)

Should see a** .deluge** directory

---

### Post by ThrobbingBrain66 on 2007-10-28
As I said in my post above, the deluge settings folder is located in /home/USERNAME/.config/deluge

---

### Post by haggus on 2007-10-28
Thanks renaming the /.config/deluge did the trick It works fine now.

---

### Post by Maestro23 on 2007-10-28
> **haggus said:**
> Thanks renaming the /.config/deluge did the trick It works fine now.

Good deal, pleas mark this SOLVED via the Thread Tools.

Thanks. :)

---

