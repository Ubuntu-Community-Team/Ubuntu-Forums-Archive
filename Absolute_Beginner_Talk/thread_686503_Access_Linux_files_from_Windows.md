---
title: "Access Linux files from Windows"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by mvashi on 2008-02-03
Here's my setup

Dual boot system 
Hard disk 1 ( 200 gb ) has Win XP
Hard disk 2 (100 gb) has Unbuntu 7.10
Hard disk 3 is an external  200 GB USB drive 

Unbuntu can see and write to XP HD
XP does even know the Ubuntu HD is there ... This is what I want to access from XP
XP can read/write delete files in the External drive.
Unbuntu mounts/sees the external drive but any attempt to create or delete or move files shows 
that the drive is a read only one

tried chmod 777 media/FAT32 -R ( FAT32 is what ubuntu and xp knows the external drive to be)
in the terminal session

starts scrolling thru all the files and folders 'changing permissions .read only system'
 also tried 
sudo chmod 777 media/FAT32 -R and the same thing happens but the 'permissions ' are not really changed

So now I need help in two things

1) Get XP to see and access files from my Ubuntu hard disk
2) ability to read/write/delete ( in short the whole works) files on my external drive from Ubuntu

Thank you

---

### Post by szymon_g on 2008-02-03
hm...
what filesystem your ubuntu-partitions has :?
if its ext3, you *prabably* may acces it through total commander + some plugins (but, personally, i never tried it)
and, btw, i see no reason why you cannot access your external disc from ubuntu :/


btw, are you sure its fat32 disc :? maybe thats ntfs :?

---

### Post by jaytek13 on 2008-02-03
Here's a nice program that allows you to access data on linux partitions from windows:

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by mvashi on 2008-02-03
Properties of my FAT32 shows up as vfat system

---

