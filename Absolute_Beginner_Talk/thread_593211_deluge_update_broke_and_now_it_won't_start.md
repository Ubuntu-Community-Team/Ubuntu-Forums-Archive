---
title: "deluge update broke and now it won't start"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-10-26
Deluge kept popping up telling me the latest version was available and it wouldn't stop telling me each time I started up deluge even though I didn't want to upgrade.  I tried looking around the settings for it to stop telling me.  So I finally just updated and I had some active torrents and now I've rebooted a few times and when I open up deluge it closes down right away.  I opened it up in the command line and this is what it says.......any suggestions?  I really don't want to start the download all over again since it took me almost 2 days to get to 90% complete

$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin NetworkHealth
Initialising plugin WebUi
Initialising plugin WebSeed
Initialising plugin EventLogging
Initialising plugin TorrentNotification
Initialising plugin Scheduler
Initialising plugin BlocklistImport
Initialising plugin TorrentCreator
Initialising plugin SpeedLimiter
Initialising plugin DesiredRatio
Initialising plugin TorrentPeers
Initialising plugin MoveTorrent
Initialising plugin TorrentFiles
Initialising plugin Locations
Initialising plugin TorrentSearch
Initialising plugin NetworkGraph
Initialising plugin ExtraStats
Initialising plugin SimpleRSS
Applying preferences
Starting DHT...
Showing window
Loading ExtraStats plugin...
Loading TorrentPeers plugin...
Loading TorrentFiles plugin...
Loading TorrentNotification plugin...
Loading TorrentCreator plugin...
terminate called after throwing an instance of 'libtorrent::invalid_handle'
  what():  invalid torrent handle used
Aborted (core dumped)

---

### Post by mikewhatever on 2007-10-27
Remove it and then reinstall.

---

### Post by bone2006 on 2007-10-27
I went into the config directory a few times, rename it, ran it again......step by step

The problem is the blocklist plugin.  It crashs at start.  I tried using another blocklist from the three they have on their site, first I was using safepeer, but I tried peer guardian..........samething.  It crashes at startup each time.  I'm guessing it's a bug?
It works fine unless I use this plugin feature, which I really liked.

---

### Post by bone2006 on 2007-10-27
after spending hours instailling, reinstalling playing with the configuration.  I found out that right now the only thing working when I use the blocklist plugin from [http://dev.deluge-torrent.org/wiki/BlocklistPlugin](http://dev.deluge-torrent.org/wiki/BlocklistPlugin)

is the first option.  When I'm there if I click on safepeer the site is down, so that could be a reason for safepeer not working.  The other two links work, but peerguard just hangs up when trying to download and once this happens deluge I have to kill and restarting it doesn't work I have to remove the config folder and start all over again configuring it.

So right now I'm running ubuntu 7.04 64 bit edition with the 64bit latest deluge 0.5.6 and the only blocklist that won't take down deluge completely useless is using [http://www.bluetack.co.uk/config/nipfilter.dat.gz](http://www.bluetack.co.uk/config/nipfilter.dat.gz) (Emule)

---

