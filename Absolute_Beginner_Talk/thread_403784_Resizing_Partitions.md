---
title: "Resizing Partitions"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-04-07
So here is the situation, I have two hard drives set up as follows:

sda:
10.24 GiB ext3 (Ubuntu install partition)
486.34 MiB swap
46.54 GiB NTFS (Storage partition)

sdb: 
93.36 GiB NTFS (Windows XP install partition)

Way back when, when I first started using Ubuntu, I didn't think it was quite up to par as far as everyday usability, so I only gave it that relatively small 10GB partition. Recently however I've found Feisty to be much improved, and so have been using it a lot more, and consequently filling up space. Currently I'm sitting at about a bit under 80% usage and things are looking tight.

How can I go about shrinking that NTFS storage partition, and giving Ubuntu more like 20GB to play with? I'm sure I could just wipe the NTFS partition and make a new, smaller, one... but I would rather not have to lose that data.

On a slightly related note, is that a good swap size?

---

### Post by PartisanEntity on 2007-04-07
Hi, I would recommend the GParted LiveCD. Boot from this CD and you will have gparted running, with it you can shrink, move, enlarge and delete partitions. It is a very handy tool:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) (download and burn to cd then boot your pc from the cd)

---

### Post by Raptor45 on 2007-04-07
Gparted can resize NTFS partitions? Without deleting data?

---

### Post by PartisanEntity on 2007-04-07
I am not sure how NTFS differs from lets say FAT32 in terms of resizing, but I have used gparted to resize a Windows XP NTFS partition without losing any data on numerous occasions.

Of course if you can back up your data it would be best to do that before you attempt this.

---

### Post by Raptor45 on 2007-04-07
Seems to have worked, though I haven't checked the NTFS yet. That said, is there any way to get Ubuntu to automatically redetect for fstab? The uuid of that partition changed it seems; I could do it manually I suppose, but automatic is nicer.

---

### Post by Gina on 2007-04-07
Yes, gparted will resize NTFS partitions without losing data - I've done that on two machines - a laptop and a desktop.  The Ununtu installation makes a dual-boot system if it detects Windows.  Ubuntu and Windows reside happily together and you can boot into either.

---

