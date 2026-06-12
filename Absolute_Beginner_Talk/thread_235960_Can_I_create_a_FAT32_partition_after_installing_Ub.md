---
title: "Can I create a FAT32 partition after installing Ubuntu?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by joeinazyes on 2006-08-14
I have installed DD 6.06 64-bit version on an 80GB hard disk.  The main partition on the drive (74.5GB) is formated in ext3, with one additional small swap partition.  Can I add a FAT32 5GB partition to an already formatted drive?  I would like to load and dual boot Windows 98SE on the 5GB partition.  I have GPARTED installed already.  Please advise.

---

### Post by GuitarHero on 2006-08-14
Yes you can but in most cases it is much easier to install windows, and then ubuntu.  Installing windows will overwrite the grub boot loader in the master boot record.  Im not sure how to get it back, there is a way.  If you do windows then ubuntu, grub sort of installs over windows and includes it so you can choose your os off of a list.  Windows doesnt do this.  You wouldnt need to make the partition with gparted(while gparted is a good partitioning tool) because windows can partition in its installer.  Have you done much with ubuntu yet?  It may be easiest to redo it as i mentioned above.

---

