---
title: "Find my music"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by stonecold23 on 2007-04-18
hi, very new to linux cant work out the file system yet. have a basic grasp though.
all my music on my pc is stored in xp
under 
(a separate partition.)
g\:philsdocs/music  

is there a way to locate this in ubuntu and simply just play the tracks. rather than waste another 80gb ripping all my music again!

---

### Post by aidanr on 2007-04-18
you have to mount the partition to browse to it, follow the guide here
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by stonecold23 on 2007-04-18
whats the difference between (ntfs) and (FAT)?

---

### Post by Voland on 2007-04-18
Try [Google]("http://www.google.ru/search?q=comparison+fat+ntfs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ru:official&client=firefox-a")
For example, [this]("http://home.earthlink.net/~lreynol929/ruXP/Misc/fatntfs.htm") and [this]("http://www.ntfs.com/ntfs_vs_fat.htm") or [this]("http://www.microsoft.com/technet/archive/ittasks/deploy/fat.mspx")

---

### Post by stonecold23 on 2007-04-18
right i write this in terminal ?

sudo mkdir /media/windows

then press enter?

then write this?

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

then press enter again

and i get an error

---

### Post by aidanr on 2007-04-18
it would help if you post the error, and also be sure to read the the general notes and how to list partition tables like the guide says to

---

