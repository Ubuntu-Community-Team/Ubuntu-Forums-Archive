---
title: "Partition question"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by PhoHammer on 2007-12-04
I have a 50 GB hard drive and i was wondering how much I should partition for Ubuntu. 

Also, Will I be able to access things such as mp3s and other files that I have in windows if I boot Ubuntu?

---

### Post by chaddiesel on 2007-12-04
It's your choice how much space to partition for Ubuntu.


> 
Also, Will I be able to access things such as mp3s and other files that I have in windows if I boot Ubuntu?

Ubuntu makes it very easy to access files from the windows partition. Just double click through the files.

---

### Post by bodhi.zazen on 2007-12-04
Ubuntu can be installed in as little as 5 or so MB, I would advise 10 Mb

Yes you can access your windows partition :

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by fineas on 2007-12-04
From [http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition) 
[I]
Ubuntu is available for PC, 64-Bit and Mac architectures. At least 256 MB of RAM is required to run the desktop install CD. Install requires at least **4 GB** of disk space.

[/I]

Usually, 5-10GB is highly recommended.Of course, you can use the whole hard disk for ubuntu :mrgreen:

---

