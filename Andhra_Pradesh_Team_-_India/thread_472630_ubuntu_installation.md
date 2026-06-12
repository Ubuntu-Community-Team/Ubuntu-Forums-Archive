---
title: "ubuntu installation"
date: 2007-06-13
forum: Andhra Pradesh Team - India
---

### Post by manuz on 2007-06-13
I've  ASUS A6Q00Va notebook, with P-M 740 1.7GHz,  533FSB/ATI X700, 512MB RAM, 80GB HDD.

I wanted to have dual boot system with Xp & Ubuntu.

I've created unallocated disk space of ~20GB and proceeded to demo with ubuntu CD.

During the installation, I've created a partition of ~19 GB for ubuntu & ~1GB of swap space.

So my hard disk partitions looked like:
C:\ ~20GB Fat32
D:\ ~40 GB NTFS
filesystem ~19 GB ext3
swap ~1GB 

However after installation I've observed an additional partition of ~400 MB named as BOOT at the end.

PROBLEM:

My notebook doesn't boot any more,  leaving me with a simple message "Error loading operating system".
Booting ubuntu from CD works & I can access the data in the other drives also.

Is there anyway to restore my XP back?
Can anybody please help me?

Thanks
manu

---

### Post by dfreer on 2007-06-14
You can:
(1) Run the recovery console on a windows XP disc and fix the MBR, but then only windows will load
(2) Either reinstall Ubuntu, or just reinstall GRUB (both of which can be done from the live CD) so that it boots Ubuntu and windows correctly.

If you need, I can give you step-by-step instructions to do either task, although with that information you should also be able to find a guide here or on google, this sort of thing occasionally happens.

I would just try reinstalling Ubuntu if you don't have any information that needs backed up on it. Also, for your BOOT partition, when you load the Live CD, can you post the output of this command?:
```
sudo fdisk -l
```
It used to be that a /boot partition was needed when dual-booting OS's (legacy, separate /boot partitions are needed for older machines that cannot boot past the 1024 limit, although it should be placing the /boot at the FRONT of the drive if this was the case), but I don't think Ubuntu Live CD would automatically make a separate boot partition.

---

### Post by manuz on 2007-06-14
> **dfreer said:**
> You can:
(1) Run the recovery console on a windows XP disc and fix the MBR, but then only windows will load
(2) Either reinstall Ubuntu, or just reinstall GRUB (both of which can be done from the live CD) so that it boots Ubuntu and windows correctly.

If you need, I can give you step-by-step instructions to do either task, although with that information you should also be able to find a guide here or on google, this sort of thing occasionally happens.

I would just try reinstalling Ubuntu if you don't have any information that needs backed up on it. Also, for your BOOT partition, when you load the Live CD, can you post the output of this command?:
```
sudo fdisk -l
```
It used to be that a /boot partition was needed when dual-booting OS's (legacy, separate /boot partitions are needed for older machines that cannot boot past the 1024 limit, although it should be placing the /boot at the FRONT of the drive if this was the case), but I don't think Ubuntu Live CD would automatically make a separate boot partition.

Thanks dfreer.
Yesterday I tried installation once again with ubuntu CD & it worked. Now both XP & Ubuntu are working.
I've made 2 modifications w.r.t disk partitions this time.
1. Earlier disk partitions  c:\(fat32) + d:\ (ntfs) + ext3 (ubuntu installation location) + linux swap space = 80GB

I was getting an error, disk is full.
So, now my partitions are: c:\(fat32) + d:\ (ntfs) + ext3 (ubuntu installation location) + linux swap space + free space = 80 GB

2. I've selected linux partition to be primary partition. Earlier it was logical drive.

Thanks for your time.
manu

---

### Post by bharadwaj on 2008-04-10
> **manuz said:**
> Thanks dfreer.
I've made 2 modifications w.r.t disk partitions this time.
1. Earlier disk partitions  c:\(fat32) + d:\ (ntfs) + ext3 (ubuntu installation location) + linux swap space = 80GB

I was getting an error, disk is full.
So, now my partitions are: c:\(fat32) + d:\ (ntfs) + ext3 (ubuntu installation location) + linux swap space + free space = 80 GB

2. I've selected linux partition to be primary partition. Earlier it was logical drive.

Thanks for your time.
manu

Cheers! thanxs for sharing your solution too with our forum members :)

---

