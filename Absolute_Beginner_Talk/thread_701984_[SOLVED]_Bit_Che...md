---
title: "[SOLVED] Bit Che..?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-19
does any1 know if bit che work on ubuntu  its a program the searches for torrents you can download it and use it so its not in a web browser, or is there anything else like it?

---

### Post by Dr. Octagon on 2008-02-19
I know that Ktorrent has an integrated search function, but I don't believe it searches as many locations from what I can tell from bit che.

---

### Post by chip! on 2008-04-07
hello,

i'm the developer of bit che and i recently got Ubuntu 7.10 setup to test Bit Che..

using the latest release of WINE, Bit Che does run and search..

i am brand new to ubuntu, but i noticed that launching the .torrents after downloading them with Bit Che was not automatic into the default torrent handler for ubuntu. after some playing around, i was able to get it working. now you can open torrents directly with Bit Che and have them open in either Ubuntu's default torrent downloader (or you can specify if you want to use uTorrent to download torrents).

Attached you will find 3 files that will let you either launch .torrents into your systems default or uTorrent (in Wine).


**For the default system torrent downloader:**

1. you need to modify the Wine registry to point to a special script to handle launching the torrent.
import the registry file "Default_System.reg" into your WINE registry to setup the .torrent handling in the registry. 

2. Then extract the "torrent_open.script" to your "C:\Program Files\Bit Che\" virtual path in WINE.

3. Now when you 'Open Torrents' in Bit Che, they will be handled by the script which launches gnome-btdownload  (by default on Ubuntu 7.10).


**For using uTorrent in Wine:**

1. Import the "uTorrent_Wine.reg" into your WINE registry.

2. Now "C:\Program files\uTorrent\uTorrent.exe" will be used to handle the opening of .torrents in WINE.



The other issue is that the ListView font is pretty small but I am updating Bit Che to allow this to be changed.

If anyone else wants to chime and help me get Bit Che running smooth on Ubuntu, please do! 

thanks,
chip
convivea.com

---

