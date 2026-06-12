---
title: "odissey with partition part 2"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2007-09-09
i had to reinstall ubuntu because i had problem with old  partition.
Now i re-partitioned my 200GB hd only for linux.
I created :

root 15GB
swap 1GB
home 184GB

but now i see that my home is very small maybe 15GB. From fdisk:
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1946    15631213+  83  Linux
/dev/sdb2            1947       24321   179727187+   5  Extended
/dev/sdb5            1947        2068      979933+  82  Linux swap / Solaris
/dev/sdb6            2069       24321   178747191   83  Linux

```

i've no idea from where /dev/sdb2 come. I've never created it!

the fstab is :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0f6112ac-8b57-4edb-8e2e-9bd5d85de0e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=385E-12F0  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=7477ba62-14af-4003-92e4-707a8d3dc7ca /media/sdb6     ext3    defaults        0       2
# /dev/sdb5
UUID=25a0d40a-e8ff-44ca-a5f8-9accbc21a662 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

i'd like to have a home of 184 GB. I spent the entire yesterday afternoom to install ubuntu because i had two blackouts and then gparted didn't see my hds and then at the end of every installing fsck said the there was an error in the root and finished for loopping.
i'm very tired i've never spent so long time for installing a linux distribution. Now i thought i re-install ubuntu instead i've a home that when i backup dvd will give me problems


Is there a way to solve this problem?
thanks

---

### Post by bone2006 on 2007-09-11
/dev/sdb6 was where you probably wanted your home, which is the bigger partition, and /dev/sdb1 is probably where you wanted the root, but it doesn't seem like you've done this.

If you don't have anything, just use gparted delete everything start over.  Create 2 ext3 partitions and then 1 swap.  Right now on a sheet of paper where the home is, then when you start ubuntu do a manual partition installation, a click on edit partition.  Change the root to \ and the other edit to home.  Put a checkmark on format them all.

---

