---
title: "Write to hdb1 (Solved)"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by LuxoDave on 2005-11-20
Hi,

I have a second hard drive on my system that I want to use to move file from Ubuntu to WinXP. I formatted it as a FAT32 drive and Ubuntu sees it as Windows Virtual Fat (vfat). I have successfully mount the drive in the /media directory and altered my fstab file so it is mounted after each reboot, however I can not write to it from Ubuntu. I tried using 
> sudo chown -R root:username hdb1/file\ name

I get an operation not permitted error for each file in the directory. What am I doing wrong?

---

### Post by aysiu on 2005-11-20
Follow these directions:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by LuxoDave on 2005-11-21
[QUOTE=aysiu]Follow these directions:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)[/QUOTE]


Ahh! Got it, thanks. I needed to change the options field to "iocharset=utf8,umask=000" from "default."

---

