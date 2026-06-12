---
title: "OK, having problems with mounting a drive"
date: 2005-06-17
forum: Absolute Beginner Talk
---

### Post by mp3guy on 2005-06-17
OK, i'm running vesion 5.04. Dual booting with WinXP. XP is on hda1, 50GB, Ubuntu is on hda3, 8.5GB and I have a fat32 partition as hda2, 15GB. Problem is, when i mount hda2, I need to use sudo in terminal to make any changes to it. Is there anyway I can unlock the drive so I can edit it like a second partition normally (which it is) or can I combine it with the hda3 partition? I have GParted for ubuntu and Partition Magic 7 for WinXP

---

### Post by aysiu on 2005-06-17
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by poofyhairguy on 2005-06-17
[QUOTE=mp3guy]OK, i'm running vesion 5.04. Dual booting with WinXP. XP is on hda1, 50GB, Ubuntu is on hda3, 8.5GB and I have a fat32 partition as hda2, 15GB. Problem is, when i mount hda2, I need to use sudo in terminal to make any changes to it. [/QUOTE]

use 

gksudo nautilus

not sudo, sudo can cause problems. 

You can do what you want...but I don't know how.

---

### Post by aysiu on 2005-06-17
Follow the steps in the link I posted.

---

