---
title: "Accessing files from ntfs partition in ubuntu"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by jay1097 on 2007-03-12
hey 
im having a lot of trouble getting access to my ntfs partition in ubuntu. i have a ubuntu 6.10 amd64, and i have a windows vista 32x partition. the partition is called sda2 (i have a SATA hdd). ive tired at least a dozen forums and nothing seems to work, sometimes i can get access to the partition but i lose it after a reboot. anyway here is some information about my harddrive setup:

here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0f8225fd-643e-4b8c-9041-2312f3f5971f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e441f1d0-fd3c-44dc-b9af-436415e7283c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

and i get this warning before it open up this doc. 
(gedit:5718): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

also here is my hdd set up
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19223   152863744    7  HPFS/NTFS
/dev/sda3           19224       24110    39254827+  83  Linux
/dev/sda4           24111       24321     1694857+   5  Extended
/dev/sda5           24111       24321     1694826   82  Linux swap / Solaris


If someone could help me get access to my vista partition (with-out it always disapering after a reboot) i would really appreciate it.

---

### Post by infol on 2007-03-12
hi!

try adding

```
 /dev/sda2 /media/vista ntfs defaults 0 0
```

to your /etc/fstab (you will have to be root to edit the file). In this case, the partition should be mounted at /media/vista - you may want to change to something else...

Good luck.

---

### Post by jay1097 on 2007-03-12
that didnt work... ive tried something very similar already but pwith media instead of vista

---

### Post by OffHand on 2007-03-12
> **jay1097 said:**
> that didnt work... ive tried something very similar already but pwith media instead of vista

```
sudo mkdir /media/vista
```

reboot

---

### Post by jay1097 on 2007-03-12
it still doesnt work!!! :(  i lose the vista partition when i reboot my pc. there needs to be something else that i am doing wrong. im somewhat new to ubuntu so mabye it is something very basic.

---

### Post by OffHand on 2007-03-12
> **jay1097 said:**
> it still doesnt work!!! :(  i lose the vista partition when i reboot my pc. there needs to be something else that i am doing wrong. im somewhat new to ubuntu so mabye it is something very basic.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by jay1097 on 2007-03-12
same problem as before i dont have aproblem accessing the hdd partition when i put in the "sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222" command, but after a reboot i no longer have access to the hdd partition. also i tired the mount parition on boot. and that didnt work at all. but i might not have been doing it right. is there an order to wheere a place the "/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0"  command, do i need to put a '#' sign infront of the command.

---

### Post by OffHand on 2007-03-12
> **jay1097 said:**
> same problem as before i dont have aproblem accessing the hdd partition when i put in the "sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222" command, but after a reboot i no longer have access to the hdd partition. also i tired the mount parition on boot. and that didnt work at all. but i might not have been doing it right. is there an order to wheere a place the "/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0"  command, do i need to put a '#' sign infront of the command.

Try sda1

---

