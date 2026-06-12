---
title: "Backup partition for both xp and ubuntu"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by lodbergs on 2006-08-09
Hi

I have a free unformated partition (~35GB) which I would like to use for backup in both WinXP and Ubunto. Is that possible and if so which fileformat should the partition be formated in?

Regards, Søren

---

### Post by Jagot on 2006-08-09
Yes it is possible.

FAT32 will allow you to use the partition without any fiddling between both operating systems.  It is possible to use other file systems but they require drivers, etc.

---

### Post by kebes on 2006-08-09
The fileformat depends on what tools you'll be using for backups. If you're going to be doing partition images, note that older versions of Ghost don't work well with the Linux ext3 filesystem, and can't write to NTFS partitions. partimage can be used in Linux to make backups of ext2 and ext3 and fat32, but doesn't work very well with NTFS.

So if you plan on using both Ghost and partimage (for instance) the backup drive should be fat32, so that you can access from both a DOS boot disk/Ghost and from a Linux LiveCD/partimage.

If your backup is more of a "copy all files to extra partition" type of solution, then again fat32 is your only real option. Fat32 can be read/written from within windows XP and within Linux without any problem. Any other format and it won't be reliable.

Only if you have a program that you know works well with all the filesystem types should you use a more advanced format (such as NTFS or ext3...).

---

### Post by lodbergs on 2006-08-09
Hi Jagot

Thank you for the swift anwser. When I select the partition and choose format I can select:
- extended 2
- extended 3 
- reiserfs
- xfs
- jfx
- windows virtual fat (vfat)
- memoryswap

I can't select Fat32. Can you help me?

I hope so :)
Søren

---

### Post by Jagot on 2006-08-09
It will be VFAT - it's the same thing.

---

### Post by aysiu on 2006-08-09
I would recommend Ext3 and [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by lodbergs on 2006-08-09
Hi again

@Jagot: thx
@kebes: thx for your help as well. I'm getting smarter each sec I spend on the board.

I'm really stunned by the number of friendly people on the board. Help is max 2 minutes away........love it :D

---

### Post by Jagot on 2006-08-09
> **aysiu said:**
> I would recommend Ext3 and [http://www.fs-driver.org](http://www.fs-driver.org)

Whatever I do I've never managed to get fs driver working, so any drives I have to share between Windows and Linux are FAT32.

---

