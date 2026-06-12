---
title: "Help with hard drive"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Rbchound on 2007-06-09
I am trying to access a SATA hd on my system.
The drive has all my photos on it.
I can't see it in Ubuntu.

The device in question is listed below is /dev/sdc1:

bman@bman-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c91b7823-329c-474c-8cd8-c2a2a59b553e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=10afda5b-811d-463c-b0af-0bdf8d7239f8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
bman@bman-desktop:~$ media@media-server:~$ cat /etc/fstab
bash: media@media-server:~$: command not found
bman@bman-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4661    37439451   83  Linux
/dev/hda2            4662        4866     1646662+   5  Extended
/dev/hda5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80032038912 bytes
240 heads, 63 sectors/track, 10338 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10337    78147688+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9730    78155200+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14596   117242338+   c  W95 FAT32 (LBA)

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9729    78148161    b  W95 FAT32

Disk /dev/sdf: 1039 MB, 1039663104 bytes
255 heads, 63 sectors/track, 126 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         126     1012063+   b  W95 FAT32

Here is my fstab:

bman@bman-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c91b7823-329c-474c-8cd8-c2a2a59b553e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=10afda5b-811d-463c-b0af-0bdf8d7239f8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

How do I mount this hard drive so I have read/write access through Ubuntu?

Any help would be appreciated!

---

### Post by taurus on 2007-06-09
Try

```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by Bohlio on 2007-06-09
If this is a NTFS partition... ```
sudo apt-get install ntfs-3g
mkdir /media/(name you want)
mount -t ntfs-3g /dev/sdc1 /media/(name you want)
```

Edit, Ahh, I probably should have read a little better :-) Fat32 not NTFS :-P My bad

---

### Post by Rbchound on 2007-06-09
Okay Taurus that worked.  I can now see the files in the media folder.  Now how do I get the drive to appear on my computer desktop?

---

