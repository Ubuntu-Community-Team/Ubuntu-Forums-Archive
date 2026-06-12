---
title: "Lost with permissions........"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-10-15
Im new to this world and Im having some problems getting these permissions going.

I connect a USB HDD to my laptop and I cant seem to wx anything in there. I tried running chmod and su but nothing works.

If there is some good reading on the web about it, please point me to it.

thanks

---

### Post by Xarok on 2007-10-15
What is the filesystem of your USB HDD? Fat32? NTFS?

If it's NTFS there may be extra software you have to install in your Linux laptop in order to use it fully.

Just a guess

---

### Post by zakeen on 2007-10-15
yeah its ntfs. So what does that mean?

---

### Post by bodhi.zazen on 2007-10-15
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

### Post by zakeen on 2007-10-15
Thanks heaps for that!

---

### Post by Kheldin on 2007-10-15
Just a note: If this drive is being used for important backup purposes, I wouldn't leave it as NTFS, especially if only a linux machine will be accessing/using it. Although there is 'generally' no problems writing to a NTFS file system in linux, its not 100% by any means.

---

