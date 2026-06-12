---
title: "oopsey ... Cannot mount volume."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-25
You are not privileged to mount the volume 'Lotus'.
why's that?

---

### Post by c-ron on 2008-03-25
The settings for the drive in your /etc/fstab file probably do not permit regular users to mount the drive.
This is normal. Get more info from the mount manual page, 'man mount' at the terminal.

---

### Post by jan quark on 2008-03-25
please post the results of there commands:

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by munch3 on 2008-03-26
> [B]jovan@jovan-desktop:~$ sudo fdisk -l
[sudo] password for jovan: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2545f9d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        5349     2008125   82  Linux swap / Solaris
/dev/sda3            5350       19457   113322510   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30b9c739

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS


jovan@jovan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=42db8128-8dd4-4dd8-a96b-701abfcbe108 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6274C7D674C7AADD /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=0E54A3B054A3994B /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=8c9989b6-0f38-46e8-b7cb-aa0901578abc none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
jovan@jovan-desktop:~$ 
[/B] .

---

### Post by jan quark on 2008-03-26
I guess you want to mount the 80 GB drive?

first install these packages to handle ntfs partitions

```
sudo apt-get install ntfs-3g ntfsprogs
```

now lets do a mount point for the new partition

```
sudo mkdir /media/datapartition
```

now mount the partition with

```
mount /dev/sdb1 /media/datapartition -t ntfs -o umask=0002,nls=utf8
```

now make a copy of the fstab file

```
sudo cp /etc/fstab /etc/fstab_backup
```

run
```
ls /dev/disk/by-uuid/ -alh
```

and copy the uuid number of the sdb1 partition

open the fstab file

```
gksudo gedit /etc/fstab
```

now add the following line to the fstab file

```
UUID=xxxxxxxxxxxx   /media/datapartition  ntfs ro,umask=0002,nls=utf8      0         0
```

save and reboot

---

