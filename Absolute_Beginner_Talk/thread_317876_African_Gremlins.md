---
title: "African Gremlins ?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by nnjond on 2006-12-13
I have a duel boot, Win 2000 and Dapper Drake on my Primary Hard Disk. Win 2000  lets me read/write to Data on my FAT 32 Ancillary Hard Disc, but Ubuntu in Disk Manager displays:

Access Path: 	none

and

Status:	Inaccessible

Is this why i can't r/wr to the same data from Ubuntu? 

Please tell me how can i remedy it?

Also; clicking on my HD 2 in Computer Browser, i get 

“Unable to mount selected volume”

and Properties reveals:

Read
Read
Read
only.

---

### Post by xyz on 2006-12-13
Could you please post here the outputs of the following command lines:
In a terminal, copy/paste this:
```
sudo fdisk -l
```
AND
```
cat /etc/fstab
```
This will give us a short overview of your HD situation.
You may want to look at this also:
[ Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by nnjond on 2006-12-13
Thankyou for your interest. Is this what u mean ?

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/hda2            3825        6374    20482875   83  Linux
/dev/hda3            2933        3824     7164990    f  W95 Ext'd (LBA)
/dev/hda5   *        2933        3783     6835626   83  Linux
/dev/hda6            3784        3824      329301   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/hdb5               2       19457   156280288+   b  W95 FAT32

Disk /dev/sda: 1030 MB, 1030750208 bytes
16 heads, 32 sectors/track, 3932 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3932     1006576    e  W95 FAT16 (LBA)
nnjond@nnjond-desktop:~$
nnjond@nnjond-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
nnjond@nnjond-desktop:~$

---

