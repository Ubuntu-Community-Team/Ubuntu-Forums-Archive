---
title: "formatted hdd"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by omerulfaruk on 2007-12-14
i

---

### Post by omerulfaruk on 2007-12-14
i formatted one of the partitions of my hdd via windoz and now i cant them in ubuntu. how can i reach them again

---

### Post by taurus on 2007-12-14
You need to mount it before you can access it.  Can you post the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
```

---

### Post by omerulfaruk on 2007-12-14
for the first one
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913       12160    82317060    f  W95 Ext'd (LBA)
/dev/hda5            1913        5099    25599546    b  W95 FAT32
/dev/hda6            5100        8286    25599546    b  W95 FAT32
/dev/hda7            8287       11218    23551258+   b  W95 FAT32
/dev/hda8           11219       12059     6755301   83  Linux
/dev/hda9           12060       12160      811251   82  Linux swap / Solaris

Disk /dev/sda: 4109 MB, 4109853184 bytes
127 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      243743      242565  2142844857    a  OS/2 Boot Manager
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(781, 103, 63) logical=(243742, 89, 34)
Partition 1 has different physical/logical endings:
     phys=(371, 68, 41) logical=(242564, 57, 7)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       69194      138387   272413365+  65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(370, 10, 16) logical=(69193, 53, 58)
Partition 2 has different physical/logical endings:
     phys=(288, 115, 51) logical=(138386, 70, 52)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       21420       21420           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(21419, 11, 51)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(21419, 11, 50)
Partition 3 does not end on cylinder boundary.
/dev/sda4          366483      366489       26464+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(366482, 30, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(366488, 122, 5)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



and second one

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=7eb4ffc6-c9a7-49f9-a9fc-7e787218ebbb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=9872-2FB2  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=D489-314E  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=20F6-E24A  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=8006-82D3  /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda9
UUID=61d82173-b1c1-4dc8-a984-eefa57e6be10 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0





and thanks alot

---

### Post by taurus on 2007-12-14
By the way, /dev/hda1 is ntfs, not vfat.  You have it mount as vfat in /etc/fstab!

Your /dev/sda drive looks all screwy.  Is that the one you plan to mount?  If you don't have anything important on that harddrive, use gparted (System -> Administration) and delete all the partitions on it.  Then, format it to whatever filesystem you want to use.

---

### Post by omerulfaruk on 2007-12-14
thanks

---

