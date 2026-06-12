---
title: "Qtparted or gparted how to resize partitions and reduce my systems overall complexity"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-10-02
sudo fdisk -l
Password:

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1         932     7486258+   7  HPFS/NTFS
/dev/hde2            1735        9728    64211805    f  W95 Ext'd (LBA)
/dev/hde3             933        1734     6442065   83  Linux
/dev/hde5            1786        3355    12610993+   7  HPFS/NTFS
/dev/hde6            3356        9728    51191091    7  HPFS/NTFS
/dev/hde7            1774        1785       96358+  82  Linux swap / Solaris
/dev/hde8            1735        1773      313204+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdh: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1   *           1        1020     8193118+   b  W95 FAT32
/dev/hdh2            1021        4865    30884962+   f  W95 Ext'd (LBA)
/dev/hdh5            1021        2040     8193118+   b  W95 FAT32
/dev/hdh6            2041        2971     7478226    b  W95 FAT32
/dev/hdh7            2972        3973     8048533+   b  W95 FAT32
/dev/hdh8            3974        4865     7164958+   b  W95 FAT32
Well here is my complex partition table for my 2 drive system. I want hde1 to increase in size as well as hde3 and I want to combine all the linux swap into one swap file. I ended up with one tiny one when I initially set up the system so I want to merge that into the active swap. I kind of want to merge all the fat 32 parts into two partitition hdh1 and 2. I understand I will have to edit fstab and grub how do I get the first part done?
Kiheikev

---

### Post by think13 on 2006-10-02
Do all of the partitions have files stored on them?
I think the first step would be to get rid of (or move) everything on the partitions you want to get rid of.  You are safe deleting partitions with nothing on them.  Back up the files you don't want to lose just in case.

The only problem you may run in to is that I don't believe you can move the start point of a partition.  I'm not sure you will have to edit grub unless you are moving or deleting the partitions with OS's on them.

---

