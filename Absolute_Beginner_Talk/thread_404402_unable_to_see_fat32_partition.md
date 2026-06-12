---
title: "unable to see fat32 partition"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by jtmedin on 2007-04-08
Ok i have created a fat32 partition but am unable to mount same. 

Here is my fdisk:
ted@teds-tower:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9601    77120001    7  HPFS/NTFS
/dev/hdb2            9602        9729     1028160    f  W95 Ext'd (LBA)
/dev/hdb5            9602        9729     1028128+   b  W95 FAT32
ted@teds-tower:~$

and here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5    /media/fat_files vfat  iocharset=utf8,umask=000  0    0
/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0


/dev/hdb5 is the fat file
Help TIA

---

### Post by taurus on 2007-04-08
What happens when you run this command from a terminal?

```
ls -la /media/fat_files
```

---

### Post by Patrick K on 2007-04-08
One thing that jumps out at me is "iocharset=utf8" . None of my 11 vfat partitions have this option set. I don't know enough to tell  you to remove it, though. I doubt there is any danger in removing it but someone with more knowledge should verify this.

---

### Post by jtmedin on 2007-04-08
ted@teds-tower:~$ ls -la /media/fat_files
ls: /media/fat_files: No such file or directory
ted@teds-tower:~$

---

### Post by taurus on 2007-04-08
```
sudo mkdir /media/fat_files
sudo mount -a
df -h
```

---

### Post by jtmedin on 2007-04-08
Ok thanks but i would like the fat_files partition when i boot.
Would like 3 drives:
winunix
winxp
win2unix

where win2unix would be the fat32 partition

---

