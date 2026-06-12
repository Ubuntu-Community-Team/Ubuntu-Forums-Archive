---
title: "Mounting Problem"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by debasishg on 2006-09-06
i'm having two HDD as hda0 and hd1 and i have installed my ubuntu in hda1. when i'm trying to mount a partition, i have go a error msg /dev/hda not found. how do i mount it

**HDA0** 
C:\WINXP    NTFS
D:\         NTFS
**HDA1**
EXT3
D:\         NTFS
E:\         NTFS
F:\         FAT32

these are my HDD structure.

---

### Post by cotcot on 2006-09-06
Your question is not very clear. Here is a suggestion to provide more info.
This is a strange layout. Generally 2 HDD are named hda and hdb (if IDE drives). Partitions on it are generally named hda1, hda2, .., hdb1, hdb2, ... . (not with a 0 such as hda0)
Your layout is strange because of this. I further do not see a swap partition which is mandatory for linux.
Could you post the result of ```
sudo fdisk /dev/hda
``` and ```
sudo fdisk /dev/hdb
``` ?

---

### Post by anaconda on 2006-09-06
You are propably mixing grub:s way of numbering hd:s (hd0 hd1...) with ubuntus way of naming hd:s (hda, hdb, hdc..)

anyway. you can mount them manually from terminal if you want.
```

sudo su
cd /mnt
mkdir hda1 hda2 hdb1 hdb2 hdb3
mount -t auto /dev/hda1 /mnt/hda1
mount -t auto /dev/hda2 /mnt/hda2
mount -t auto /dev/hdb1 /mnt/hdb1
mount -t auto /dev/hdb2 /mnt/hdb2
mount -t auto /dev/hdb3 /mnt/hdb3
```

the mkdir (make new directory) propably complains that directory already exists.. but it doesnt matter. But after doing that you can access your partitions from /mnt/hdXX..

the output of 
sudo fdisk -l /dev/hda
sudo fdisk -l /dev/hdb
would help in giving the mounting instructions..

and cotcot: 
Swap-partition isn't mandatory for linux. If you have enough memory I can't see any poin in making one, and even if you need swap you can always (later) make a swap-file to your ubuntu-partition..

---

### Post by debasishg on 2006-09-06
```
debasish@ubuntu:~$ sudo fdisk /dev/hda

Unable to open /dev/hda
debasish@ubuntu:~$ sudo fdisk /dev/hdb

Unable to open /dev/hdb
debasish@ubuntu:~$
```

this is the error msg when i'm trying.

---

