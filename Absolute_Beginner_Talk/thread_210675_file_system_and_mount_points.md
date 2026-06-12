---
title: "file system and mount points"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-07-07
I am having a hard time figuring out how to mount my fat32 drives  read/write and my NTFS drives to mount read. Does someone have a tutorial on how to navigate the file system both in terminal and in the pointy clickedy way?
I know this will tell me what is mounted... 
cat /etc/fstab
But how do I go about editing the file so that my hard drives will mount at boot time?
I am running a dual boot dapper 6.06 and Windows XP. Here is the output of the above.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

My motherboard has 4 IDE  controllers. IDE 1 and 2 are connected to cd-r and DVD-r drives with no slaves. IDE 3 has one 80 GB master and IDE 4 has a  20 GB master and 40 GB slave. Hmm now where can I get the partition table so I can post it for my next message? I do know I boot for linux from hde something...
Kiheikev
:KS Aloha!

---

### Post by araz on 2006-07-07
Here is the help you need:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

---

### Post by keheikev on 2006-07-07
Thank you very much...
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
kevin@kevinscomputer:~$
kevin@kevinscomputer:~$ sudo fdisk -l
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
/dev/hde7            1775        1785       88326   82  Linux swap / Solaris
/dev/hde8            1735        1773      313204+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdg: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1        2480    19920568+   7  HPFS/NTFS

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

Disk /dev/sda: 1039 MB, 1039933440 bytes
32 heads, 63 sectors/track, 1007 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1006     1014016+   6  FAT16
Kiheikev
aloha!

---

