---
title: "add new hdd+ backup"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by deepblue80 on 2008-04-14
Hi
I need advice on adding a new HDD + data backup. 

Current Configuration:
Ubuntu 7.01 + 80GB Maxtor IDE HDD

I want to add a new 250GB sata hdd. 

Questions:
1. How do I transfer my existing data from the 80 GB hdd to the new 250GB HDD? Step by step instructions please!
2. Can i use an ide and a sata hdd on the same system - having Ubuntu on 250GB and using the 80 GB as backup?
3. Is it possible to format the new 250 GB in two extensions - ie. Windows Xp on first partion of 125GB formatted as NTFS and Ubuntu on second partiion of 125Gb as ext3? in that case can i use the 80 gb as backup as well.

THank you for your help,
Deep

---

### Post by logos34 on 2008-04-14
> **deepblue80 said:**
> 
1. How do I transfer my existing data from the 80 GB hdd to the new 250GB HDD? Step by step instructions please!
2. Can i use an ide and a sata hdd on the same system - having Ubuntu on 250GB and using the 80 GB as backup?

Either [copy it with Gparted]("http://gparted.sourceforge.net/larry/move/move.htm"), or ghost it with [Partimage]("http://www.partimage.org/Partimage-manual_Usage") and restore it to new partition/drive.  You could also copy it with the dd command, ex.:

dd if=/dev/sda2 of=/dev/sdb2 bs=4096 conv=notrunc,noerror

> 3. Is it possible to format the new 250 GB in two extensions - ie. Windows Xp on first partion of 125GB formatted as NTFS and Ubuntu on second partiion of 125Gb as ext3? in that case can i use the 80 gb as backup as well.

yep, just use gparted on the ubuntu live cd or the Gparted live cd.  You 80 gig will be detected and added to fstab so you can access it in linux, as will your windows/ntfs partition on the 250.  You will be able to read+write to ntfs from linux by default, and you can get** fs-driver** for windows to enable you access to ext3 partitions (if, that is, you're planning a dual-boot.  In which case be sure to install windows before linux).

---

