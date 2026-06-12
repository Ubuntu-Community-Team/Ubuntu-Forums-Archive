---
title: "ubuntu installation help"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by bigun on 2007-01-25
Hi, 

My very first post from a brand new ubuntu user... who can't get it installed. 

Sorry if this sounds really stupid, but I don't know where to look.  I have a Poweredge 2300, PII 350Mhz with 256 Mb, 3x 9Gb SCSI Discs Dells with PERC - RAID.  

I have just started installing "edgy" and have gotten to partioning the disk... however the install can't detect disks...

It asks me if i know the driver i need... but I don't have a clue... I have tried googling to get the specs, but have been at this since 1900... it's now 2044...and still nothing. 

Please, can anyone help. 
Thanks.

---

### Post by Happy_Man on 2007-01-25
Boot from the LiveCD, go to a terminal, and input this:

```
sudo fdisk -l
```

and post the results here. We'll work from there. ;)

---

### Post by steve.horsley on 2007-01-25
I've seen the same thing. I think Ubuntu doesn't recognise the custom SCSI controller. So it's not a hardware problem with your machine, in case you wondered. I don't know what to do about it though.

---

### Post by bigun on 2007-01-26
Here is what I get...

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 8984 MB, 8984199168 bytes
255 heads, 63 sectors/track, 1092 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         127     1020096    6  FAT16
/dev/sda2             128        1092     7751362+   5  Extended
/dev/sda5             128        1092     7751331    7  HPFS/NTFS

Disk /dev/sdb: 8984 MB, 8984199168 bytes
255 heads, 63 sectors/track, 1092 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1092     8771458+  87  NTFS volume set

Disk /dev/sdc: 9120 MB, 9120514048 bytes
255 heads, 63 sectors/track, 1108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1108     8899978+  87  NTFS volume set

```

---

