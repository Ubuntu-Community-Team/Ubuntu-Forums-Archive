---
title: "Can I create a FAT32 partition after installing Ubuntu?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by joeinazyes on 2006-08-14
I have installed DD 6.06 64-bit version on an 80GB hard disk.  The main partition on the drive (74.5GB) is formated in ext3, with one additional small swap partition.  Can I add a FAT32 5GB partition to an already formatted drive?  I would like to load and dual boot Windows 98SE on the 5GB partition.  I have GPARTED installed already.  Please advise.

---

### Post by benuski on 2006-08-14
If you're going to carve the hunk for your FAT32 partition out of your main Ubuntu partition, I'm pretty sure you need to do this from a livecd, as you have to have the partition unmounted to be able to change it.  At least, thats the way it seems to be with GParted.  So, I'm fairly sure the Ubuntu livecd comes with GParted, or, alternatively, GParted itself comes with its own [livecd]("http://gparted.sourceforge.net/livecd.php") version, and that should be able to help you.

---

