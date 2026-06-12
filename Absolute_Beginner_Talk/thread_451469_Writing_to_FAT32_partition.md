---
title: "Writing to FAT32 partition"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-05-22
I have two drives, both formatted FAT32. They are master & Slave.
Win ME & Ubuntu are on partitions of the Master.
I have mounted both drives and edited fstab accordingly. I can browse the drives but still cannot write to them. I have tried saving images from Firefox and saving text documents.

---

### Post by taurus on 2007-05-22
Can you post the output of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Neil Purling on 2007-05-22
Here you are:

neil@neil-desktop:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16704   134174848+   c  W95 FAT32 (LBA)
/dev/hda2           16705       30118   107747955   83  Linux
/dev/hda3           30119       30401     2273197+   5  Extended
/dev/hda5           30119       30401     2273166   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2434    19551073+   c  W95 FAT32 (LBA)
neil@neil-desktop:~$

---------------------------
neil@neil-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /mnt/FAT32      vfat    defaults        0       0
/dev/hdb1       /mnt/Slave      vfat    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
neil@neil-desktop:~$

---

### Post by taurus on 2007-05-22
> **Neil Purling said:**
> Here you are:

neil@neil-desktop:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16704   134174848+   c  W95 FAT32 (LBA)
/dev/hda2           16705       30118   107747955   83  Linux
/dev/hda3           30119       30401     2273197+   5  Extended
/dev/hda5           30119       30401     2273166   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2434    19551073+   c  W95 FAT32 (LBA)
neil@neil-desktop:~$

---------------------------
neil@neil-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /mnt/FAT32      vfat    defaults        0       0
/dev/hdb1       /mnt/Slave      vfat    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
neil@neil-desktop:~$

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove these two lines

```
/dev/hda1       /mnt/FAT32      vfat    defaults        0       0
/dev/hdb1       /mnt/Slave      vfat    defaults        0       0
```
 and replace them with these two new lines.

```
/dev/hda1       /mnt/FAT32      vfat      iocharset=utf8,umask=000      0       0
/dev/hdb1       /mnt/Slave      vfat      iocharset=utf8,umask=000      0       0
```
Save the changes.  Then, reboot.  

Now, you should be able to write to these two partitions, /mnt/FAT32 & /mnt/Slave.

---

### Post by Neil Purling on 2007-05-22
Quote by taurus: Now, you should be able to write to these two partitions, /mnt/FAT32 & /mnt/Slave.

Taurus you are right, I can.

---

