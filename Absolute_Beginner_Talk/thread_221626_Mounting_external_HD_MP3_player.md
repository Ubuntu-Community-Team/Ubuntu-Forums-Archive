---
title: "Mounting external HD MP3 player"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-23
I have an mp3 player of the hard drive variety.  I *should* be able to make it show up as if it were just an external hard drive with a bunch of mp3s on it.  When I plug it in, it doesn't show up in file system.  How do I mount it so that it is recognized?  I don't even care about syncing, I don't do that.  I just want to be able to copy and paste.  All I can think is that it might be NTFS, but it should still mount and read, just not write...right?

---

### Post by Silver Streak on 2006-07-23
You might have one of the players that uses MTP, AKA Music Transfer Protocol, AKA another way to prevent Linux users from leading normal lives. I have a Creative Zen Microphoto, and it uses MTP, so I have not been able to sync it *yet*. Although I do not know if you can mount such a player, someone has been working on a Linux MTP on Sourceforge, and someone here wrote a [url=http://www.ubuntuforums.org/showthread.php?t=135845]howto for getting MTP players to work in Ubuntu.

SS

---

### Post by macogw on 2006-07-23
It's a Philips GoGear HD6330.  There's a project on SourceForge called golb (GoGear On Linux Boxes), but it requires two dependencies (SQLite 2.x and something lib...forget what), but I can't find them on SF or using apt-get.


also: [http://opengogear.sarovar.org/](http://opengogear.sarovar.org/) 
still don't know how to mount it though (doesn't show up in file system folder to right-click "mount" or anything like that)

---

