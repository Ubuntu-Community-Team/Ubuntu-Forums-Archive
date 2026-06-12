---
title: "Cannot see non os drive in apps"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Atlasgrl on 2007-04-05
Ok, I am very new to Linux so forgive my ignorance.  I just installed Ubuntu 6.10 onto a drive that is also running windows 2000.  I have another drive that contains all of my music files as well as some other stuff but has no os currently installed.  In the device manager of Ubuntu and in fstab I can see the non os drive (although fstab says something about an error), but if I try to access this drive from any application (rythmbox, etc) its not there and so I have no access to my music files.  Any help?
Below is a paste of fstab exactly as it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=7538e392-b324-4f91-aa70-1f1ac3b886b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0EE8E873E8E85B0B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=c3086ca9-af6f-4328-8ef4-ecfdc511a2ac none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Atlasgrl on 2007-04-05
Sorry, fdisk is the one that mentions the error.  here it is:



Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1021     8195008+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            1022        1992     7799557+  83  Linux
/dev/hda3            1993        2884     7164990   83  Linux
/dev/hda4            2885        3267     3076447+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80054059008 bytes
16 heads, 63 sectors/track, 155114 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?      216399     1904881   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?      723265     1262922   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?      167316      167316           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdb4         2671568     2671619       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

