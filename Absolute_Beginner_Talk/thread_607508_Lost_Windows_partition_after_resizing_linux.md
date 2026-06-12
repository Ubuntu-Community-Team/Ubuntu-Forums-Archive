---
title: "Lost Windows partition after resizing linux"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Nuodaz on 2007-11-09
Hello, I use Ubuntu 7.04 and got this problem. I decided to make new partition for /home from ext3 part. free space. I booted Dapper drake liveCD, resized linux partition using resize2fs, made two partition without data lost, and accidently ran fsck -f /dev/hdb for whole drive, it showed many errors and fixed that. After that, i see raw partition in windows Xp, in linux its fat32? How to solve it?

---

### Post by Nuodaz on 2007-11-09
I tried Active Partition Recover from Hirens boot cd, sector 0, boot sector error, its on second hard disk, i guess fsck changed first sectors, and dont know how to restore that, so i could see my FAT32 partition with all data :/

---

### Post by Nuodaz on 2007-11-09
Please help, i want to get back my 64GB partition :(

---

### Post by Pulka on 2007-11-09
easy...

download Super Grub Disk. Burn it to a CD, boot from it

---

### Post by Nuodaz on 2007-11-09
And it will recover my FAT32 partition? I can boot into Ubuntu, and WinXP, whis is on first hdd.

---

### Post by Pulka on 2007-11-09
if i understood it well, that partition is there. The problem is grub doesn't know where it is. That cd must fix it.

---

### Post by Nuodaz on 2007-11-09
Sorry, but i think confused you. My system is: 
/dev/hda1  NTFS (WinXP Professional)
/dev/hdb1 (FAT32 LBA)
/dev/hdb2 swap
/dev/hdb5 ext3 
/dev/hdb6 ext3
Hmm, will try  that GRUB disk..

---

### Post by az on 2007-11-09
From your descrition, you changed the partition table, but the filesystems are still the same and still there.

It is irrelevant what type of partition it is saying it is.  That does not determine what filesystem is there.  The partition table along with the partition type will help your motherboard, the bootloader and the OS find, mount and boot the partitions, though.

All you need to do is fix your partition table.  Use testdisk or parted from a live cd.


You can use Ubuntu-rescue-remix

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

