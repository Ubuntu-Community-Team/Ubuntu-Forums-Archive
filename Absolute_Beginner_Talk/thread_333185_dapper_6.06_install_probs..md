---
title: "dapper 6.06 install probs."
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by wilcan34 on 2007-01-07
Hi Everyone,
Have a 6GHDD.Works well with Dapper6.06LTS.
Wanted to get some more capacity installed 30G HDD.
Dapper will install to 6G Drive.
Freezes when trying to install on 30G drive.
Install right up to the partitioner then Freezes.No flashing Green Light in CD Drawer.

dudo fdisc-i
Disk /dev/hda: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         752     6040408+  83  Linux
/dev/hda2             753         788      289170    5  Extended
/dev/hda5             753         788      289138+  82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            3203        3419     1743052+  82  Linux swap / Solaris
/dev/hdb2               1        3202    25720033+   5  Extended
/dev/hdb5               1        3202    25720002   83  Linux

Partition table entries are not in disk order

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Have I got it set up right?
Are the permissions correct?
Any Help would be appreciated,
Thanks
Wilcan

---

