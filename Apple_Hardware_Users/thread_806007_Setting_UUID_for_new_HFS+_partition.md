---
title: "Setting UUID for new HFS+ partition"
date: 2008-05-24
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2008-05-24
I'm working up a triple boot machine and it looks like HFS+ is the common file system.  

For /etc/fstab to be happy it looks like it needs a UUID for the partitions.  How do I create and apply one to HFS+ partitions?  

Nothing included in the package hfsprogs jumps out as doing this.

---

### Post by sisco311 on 2008-05-24
Use the blkid command to get the uuid of the partition.
```
sudo blkid /dev/sd**XY**
```replace XY with the partition number.

But you can use /dev/sdXY in the fstab.
For example:
> # /dev/sda3
UUID=e8cb3436-31aa-4238-a432-6b04713016a8 /media/arch     ext3    relatime,defaults        0       2
--->
> /dev/sda3 /media/arch     ext3    relatime,defaults        0       2
Both are valid fstab enrties,

EDIT:
use
```
sudo fdisk -l
```
to list your partitions.

---

