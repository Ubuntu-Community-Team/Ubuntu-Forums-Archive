---
title: "Dual-Boot Mac OS 10.4.9 / Feisty Fawn"
date: 2007-07-07
forum: Apple Intel Users
---

### Post by Remix_eyeballs on 2007-07-07
Im trying to dual boot Mac OS Tiger and Ubuntu 7.04.  The installation give me an error:

No root file system is defined.
Please correct this from the partitioning menu.

So I'm stuck at the partition setup.  The partitions are as follows:

/dev/sda/
  free space               *no check* 0 MB
  /dev/sda1   efi          *no check* 209 MB    209 MB
  /dev/sda2                *no check* 46170 MB  21400 MB
  /dev/sda3   swap      *no check* 257 MB     unknown
  /dev/sda4   ext3   /boot  *check* 2001 MB   unknown
  /dev/sda5   fat32           *check* 31387 MB unknown
  free space               *no check* 0 MB


I'm using BootCamp.  My computer specs:
MacBook
2 gh processor
2 gb ram
80 gb hd
white

---

### Post by cyberdork33 on 2007-07-07
you are going to get errors with more than 4 primary partitions. during the install you need to set the mount points of the partitions. your ubuntu partition should be mounted as '/' this will identify it as the root partition

---

### Post by ronocdh on 2007-07-07
> **cyberdork33 said:**
> you are going to get errors with more than 4 primary partitions. during the install you need to set the mount points of the partitions. your ubuntu partition should be mounted as '/' this will identify it as the root partition
Yes, there sure are a lot of partitions in that setup! Why the FAT32 party? You're not triple booting with WinXP, are you?

---

### Post by Remix_eyeballs on 2007-07-07
ronocdh,  I'm dual-booting unbuntu.

---

### Post by cyberdork33 on 2007-07-07
I think the fat32 is a shared partition?

You have to lose the swap if you want the fat32 partition.

---

### Post by Remix_eyeballs on 2007-07-08
Is there something else I should use other than fat32?

And for the 257MB & 2001MB partitions, what should I mount them as?

---

### Post by Oliver Barker on 2007-07-08
first you need to partition your hard drive with boot camp then boot linux of CD then install it as usual and create a ext/3 one with all the available space on the new hard drive minus 512mb then make the swap one with 512, you should only have dev/sda1 dev/sda2 and the other two you just created.

---

### Post by Remix_eyeballs on 2007-07-08
Thanks.  You help me alot!

---

