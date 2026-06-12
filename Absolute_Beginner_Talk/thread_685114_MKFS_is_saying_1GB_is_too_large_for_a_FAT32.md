---
title: "MKFS is saying 1GB is too large for a FAT32"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by nathanscottdaniels on 2008-02-01
I am trying to partition my 2GB flash drive (/dev/sdb) into two 1GB primary partitions for no purpose other than learning and showing off to my less-geeky friends.  Here is what i did so far:

I used fdisk to delete the previous partition and made two new ones, both 1GB (well one is actually .999GB) and both with a system id of c (FAT32).  

I wrote the new partition table to the drive.

I type in 
```
umount /dev/sdb2
mkfs.vfat /dev/sdb2
```

but I get this error:

```
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Attempting to create a too large file system

```

I am 99.99% certain that FAT32 can handle up to 2.5TB.  And I am sure that 1GB < 2500GB.  So what is wrong?

---

### Post by bluewraith on 2008-02-01
Have you checked the actual drive size? Most drives that state 2GB are actually 2000meg, instead of the 2048meg that they should be. Marketing ploys and all..

---

### Post by nathanscottdaniels on 2008-02-01
Yes it is actually 2GB.  And would that really matter?

---

### Post by taurus on 2008-02-01
What happens if you format /dev/sdb2 as vfat from gparted (System -> Administration)?

---

### Post by nathanscottdaniels on 2008-02-01
Wow I didn't know Linux had a GUI-based partitioning tool.  GParted is so much easier!  I managed to get it to work.  Thanks.

---

