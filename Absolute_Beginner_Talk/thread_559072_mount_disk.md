---
title: "mount disk"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by gramsyn on 2007-09-24
The disc which runs Ubuntu has 2 partitions and they are both mounted automatically when the system starts. I have a second disc (with 2 partitions) which aren't mounted automatically. How can I fix that. (When the system starts I want to see all the 4 partitions automatically).

How can I name them (instead of disk, disk1 etc., I want to label the partitions like music, files etc.)

---

### Post by Pumalite on 2007-09-24
Post:
sudo fdisk -lu
cat /etc/fstab

---

### Post by gramsyn on 2007-09-25
I posted these lines in the terminal, but the discs aren't mounted when starting the system

---

### Post by alienexplorers on 2007-09-25
Try reading:
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Compyx on 2007-09-25
What Pumalite meant was to post the output of those command here in this thread, preferably surrounded by [code] tags.

---

### Post by gramsyn on 2007-09-25
The output is:

[B]
 sudo fdisk -lu[/B]


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           16065    20482874    10233405    f  W95 Ext'd (LBA)
/dev/hda2        20482875    59552954    19535040   83  Linux
/dev/hda3   *    59552955   153276164    46861605    b  W95 FAT32
/dev/hda4       153276228   156296384     1510078+  82  Linux swap / Solaris
/dev/hda5           16128    20482874    10233373+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   208491569   104245753+   b  W95 FAT32
/dev/hdb2       208491570   488392064   139950247+   b  W95 FAT32


[B]
~$ cat /etc/fstab[/B]


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=ab13e529-3173-4b72-8605-2286b26f1f5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=9214-FFE0  /media/backup   vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=464E-C0D7  /media/files    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=4650-1BA3  /media/music    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=D85016E75016CC5E /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=4b5b248c-0641-4357-925f-7a5ca422b64b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda5 /media/hda5 ntfs ro,user,fmask=0111,dmask=0000 0 0

---

### Post by Kowalski_GT-R on 2007-09-25
follow these instructions, worked a treat for me:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

ciao,

Andre

---

### Post by Pumalite on 2007-09-25
According to fstab, they are mounted. Post:
mount

---

