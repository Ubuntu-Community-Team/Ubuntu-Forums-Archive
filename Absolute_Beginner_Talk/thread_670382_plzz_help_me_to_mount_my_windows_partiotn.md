---
title: "plzz help me to mount my windows partiotn"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-01-17
here r my partitions
Disk /dev/hda: 61.4 GB, 61492838400 bytes
16 heads, 63 sectors/track, 119150 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23655    11922088+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           23668      104375    40676580+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3          104375      119149     7446127+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           23668      103674    40323150    7  HPFS/NTFS
/dev/hda6          103674      104375      353398+  82  Linux swap / Solaris


here is the copy pf fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a1b67225-62e5-41f2-a858-46e076380009 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=da3dc3e2-64ce-481f-a4ed-28b3d57460fa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

here i cannot see any mention of hda and hda 5 where my windows partiotn are there
plzz help me

---

### Post by phidia on 2008-01-17
The Ubuntu docs [here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28mount%29%7C%28ntfs%29%7C%28partition%29") should help.

---

