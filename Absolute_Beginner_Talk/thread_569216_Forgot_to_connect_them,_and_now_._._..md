---
title: "Forgot to connect them, and now . . ."
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by larry19l on 2007-10-06
Hi Folks,
I forgot to reconnect an eSATA drive so now I need to know how to add it to fstab manually
because when I try to mount it from the "computer" icon menu (shell) it comes up in R/O mode Root user.

I also just added a Plextor 810UF via USB port and I would like to add that manually too.
But I'm going to connect it via 1394 port as soon as the cable shows up (tuesday?)!
Plextor does NOT include a firewire cable, just USB. A miserable $3.00 cable they couldn't include?!!!

Anyway, here's output of sudo fdisk -l that shows only the internal 60g and CDrom plus the 80 and 120 USB pocket drives. The eSATA drive is a Seagate 400g. 

So the question is... How do I get the drive hardware info  for these 2 drives to put in fstab ?


++++++
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3504    28145848+   7  HPFS/NTFS
/dev/hda2            3505        7134    29157975   83  Linux
/dev/hda3            7135        7296     1301265    5  Extended
/dev/hda5            7135        7296     1301233+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9728    78140128+   c  W95 FAT32 (LBA)
++++++

---
Larry.C

---

### Post by MrFSL on 2007-10-06
what is your output from the following:
```
mount
```
and
```
sudo cat /etc/fstab
```

---

### Post by larry19l on 2007-10-06
larry@R4100LC:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/WDP 120G type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdc1 on /media/WDP 80G type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
larry@R4100LC:~$ 

larry@R4100LC:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=6f2ff832-0f65-487d-b88c-9dbd07396b9b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0bc3b3f0-a2dc-4846-b057-edaa9f11c891 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
larry@R4100LC:~$

---

### Post by larry19l on 2007-10-06
Here's the latest...
---
skip the previous post
---
The Plextor is there (installed Brasero but havent tried it yet).
larry@R4100LC:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdc1 on /media/WDP 80G type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdb1 on /media/WDP 120G type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sda1 on /media/Seagate 400 type ntfs (rw,nosuid,nodev,umask=222,utf8)
larry@R4100LC:~$ 

larry@R4100LC:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=6f2ff832-0f65-487d-b88c-9dbd07396b9b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0bc3b3f0-a2dc-4846-b057-edaa9f11c891 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
larry@R4100LC:~$

---

### Post by MrFSL on 2007-10-06
you might just need to:

```
sudo chmod 777 /dev/sda1
```

...etc...
(As long as you have ntfs support configured correctly.)

---

