---
title: "Getting Ubuntu on a Dell Inspiron 1520 - Partition Issues"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Haggisfarm on 2008-02-11
I just received a new Dell Inspiron 1520 with Windows XP today, and the first thing I did was boot up GParted and attempt to reallocate space from my primary boot partition in order to set up a separate partition to install the latest release of Ubuntu on. The problem that I ran into however, was when I tried to take the newly unallocated space on my HDD and create a new Primary Partition too put Ubuntu on. Apparently I am only allowed 4 primary partitions. What i'd like to know is what partitions can be deleted, or otherwise, what partitions can be converted into extended partitions? Here is a list of currently active and healthy partitions:
Unlabeled FAT volume in an EISA Configuration with a capacity of 78 MB
Unlabeled FAT32 volume in an unknown partition with a capacity of 3.29 GB
(C:/) NTFS volume system drive with a capacity of 177.01 GB
(F:/) FAT32 volume with a capacity of 3.81 GB
MEDIADIRECT FAT32 volume with a capacity of 2.49 GB
newly unallocated space of 50.00 GB

I'd rather not lose the Dell Media Direct if I don't have to but I'd rather have Ubuntu that it if I must. I've been looking around and I'm not at all sure what the functions of the other partitions are. I'd like to convert them into extended partitions, but I'm not sure if that would lock my computer into no longer functioning. It should also be mentioned that one of the partitions is already displayed as a extended partition within GParted. On a final note, can Ubuntu be run off of an extended partition? if so, that would make it much easier to put this all together.

Thanks in advance

---

### Post by dstew on 2008-02-11
Ubuntu can be installed and run off a logical (extended) partition. I would like to see your partition table in Linux format. Boot the Ubuntu Live CD (do you have one yet?) open a terminal and enter```
sudo fdisk -l
```

---

### Post by oedha on 2008-02-11
post the result of fdisk -l
i only using 1 primary and the other are on extended including linux

---

### Post by Haggisfarm on 2008-02-11
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11       23117   185606977+   7  HPFS/NTFS
/dev/sda3           29645       29970     2618595    f  W95 Ext'd (LBA)
/dev/sda4           29971       30401     3462007+  db  CP/M / CTOS / ...
/dev/sda5           29645       29970     2618563+  dd  Unknown

---

### Post by louieb on 2008-02-11
Looks like you have unallocated space between your XP partition sda2 and the extended partition sda3.
Fire up the GParted CD.

You need to grow extended partition sda3 to the left to fill the unallocated space. Then you can use that space to create logical partitions for the install and swap.

Good luck.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by Haggisfarm on 2008-02-12
So i fired up GParted, and reallocated the unused space to the extended partition,and when i was creating the logical drive, i made a mistake, and wiped my hard drive... oh well, i'm now installing Ubuntu normally on a primary partition, thanks for your help!

---

