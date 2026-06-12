---
title: "SATA Drive troubles"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Rotaj on 2007-04-01
I am having troubles with a 250 gb sata. I am dual booting Ubuntu(Edgy AMD64) and XP. 

The XP partition is 30GB and Ubuntu is 30Gb w/2Gb swap. I would like the rest to be a FAT32 partition so I can access photos & music from both OS's. XP won't format a FAT32 larger than 32 GB and Gparted sets up the partition but won't format it. 

My last blunder was I tried to format it from DOS. DRDOS would not format it, so from fdisk I deleted the FAT32 partition trying to force DOS to recognize and therefore format the Fat32.

I am now getting a Grub error (#17) 

I am currently running from my live disk. I know Gparted is on this disc. Short of reinstalling Ubuntu, how do I access Gparted. And can I fix the Grub issue from the live disk] (*,)

---

### Post by Rhubarb on 2007-04-01
While it is possible to format a 188GB FAT32 partition, it's not going to be terribly straight-forward.
As indeed you've found out that windows will not format anything above 32GB as FAT32, there are 3rd party FAT32 formating utilities out there (I've never used them though).

Your best bet is to make either a 188GB EXT3 partition, or a 188GB NTFS partition.
If you go for EXT3, then you'll need a windows driver that allow it to read EXT3:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
(This driver will also work for EXT3 (It's made for EXT2))

The other way, would be to use NTFS, and get Ubuntu to read (and write) to NTFS, is to use NTFS-3g:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

GParted can be found on the live CD in:
System --> Administration --> GNOME Partition Editor

If need be, a more up-to-date GParted Live CD can be downloaded from:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It is possible repair your GRUB off the Live CD, but I've never done it before (hey, I don't use windows at all now).
Do a search here on the forums to find out more info, or just re-install Ubuntu.

---

### Post by Duck2006 on 2007-04-01
In the terminal

sudo gparted

That sould open geparted for you

---

### Post by Rotaj on 2007-04-01
Thank you for the help.
Do you know which file system is easier with read/write access from the other  operating system?

---

### Post by Rhubarb on 2007-04-01
Yes, format it as EXT3 (using GParted), then in windows install:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

It's very easy to do :)

---

### Post by amlife on 2008-04-09
I think the best thing to do it to enable windows to read and write to EXT3 drive .. which you can creat to hold your shared files between windows and linux.

you can do this buy installing this free tool on your windows OS.

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

it is free program worth donating to it.

---

