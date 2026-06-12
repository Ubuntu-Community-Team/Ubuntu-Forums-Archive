---
title: "How do I mount EZ-Drive (FAT32) Filesystem?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by imtopaz1 on 2007-01-28
Hello.
I have a problem of mounting an external HDD drive.
The file system of the HDD is FAT32 and it has no problem in windows.

So I tried to mount it, but I failed and I found linux tells its file system is EZ-Drive.

> root@XXX:/media/usb# mount -t vfat /dev/sda1 /media/usb
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


> [17182264.832000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17182969.480000] cramfs: wrong magic
[17182969.576000] VFS: Can't find ext3 filesystem on dev sda1.
[17182969.580000] FAT: invalid media value (0x7c)
[17182969.580000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17183742.404000] FAT: invalid media value (0x7c)
[17183742.404000] VFS: Can't find a valid FAT filesystem on dev sda1.


Here is the result of fdisk -l

> Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1559    12522636   83  Linux
/dev/hda2            1560        4982    27495247+   f  W95 Ext'd (LBA)
/dev/hda5            1631        3606    15872188+   b  W95 FAT32
/dev/hda6            3607        4982    11052688+   b  W95 FAT32
/dev/hda7            1560        1630      570244+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1023     8217243   55  EZ-Drive

I have tried to find solutions on this issue and I found a post. It says I need to add 'hdd=remap' on kernel command. So I did it but I can't still mount the device.

> root@XXX:/media/usb# dmesg | grep remap
[17179569.184000] Kernel command line: root=UUID=bb8f6f9a-13e1-4626-b3a4-c733ffa6a76b ro quiet splash hdd=remap
[17179569.184000] ide_setup: hdd=remap

Does anyone know how to solve this problem? I need your help :confused:

---

### Post by bremner on 2007-05-15
I have exactly the same problem on sda as well except my disk is NTFS.
I have tried the sda=remap fix as well to no avail.
Any help would be gladly appreciated.
Bear in mind that the disk on sda is actually one of two disks on my ite 8212 disk controller and that is the ONLY disk shown in fdisk -l.
Thanks in advance.

---

