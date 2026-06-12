---
title: "copy files from HFS+"
date: 2007-08-18
forum: Apple PPC Users
---

### Post by cortomaltese86 on 2007-08-18
Hi,
I use a LiveCD of Ubuntu (last version) on my iBook G4, because the yet installed mac os x (panther) didn't get started. From nautilus I can only read the HFS+ files, but I want to copy all them to an external hard disk.
What I should do?

ps sorry for my english

---

### Post by Backharlow on 2007-08-18
I had this issue too. The "application" that mounts HFS+ is called hfsplus, and by default it mounts in read-only mode. What I did is created a new directory in the /media directory, and then added a line for the disk I wanted to mount to the fstab file which is in /etc. This file contains custom rules for how and where disks should be mounted when Ubuntu finds them. The line I have for my Mac harddrive is this:

/dev/sdc5 /media/macdisk hfsplus rw,user,noauto 0 0

Lets look at this line because you'll have to customize it.
The disk itself is detected at this directory  /dev/sdc5, I found this out by connecting the mac disk and letting it mount as read only, and then looking at the actual location where it mounted it to. in this case, it is /dev/sdc5. For you, it may be different.
The line forces hfsplus to automatically mount /dev/sdc5 to the directory I made; /media/macdisk with the correct read-write permissions. Once the line is in that fstab file, it will do this by itself every time I plug in the disk.
On problem, hfsplus will not write to journaled HFS disks. What I did was back up the contents of the disk, then reformat the disk as non-journalled HFS using the Apple Disk Utility application. If its your OSX boot disk, doing that might be impossible for you. Also, if it is Panther, you can do non-journaled for your system boot image, but Tiger (10.4) wants to do journaled as default.

Your English is not bad at all.

---

