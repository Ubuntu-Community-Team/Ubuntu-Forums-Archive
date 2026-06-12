---
title: "[SOLVED] invalid mount option"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by hj82 on 2008-02-26
I'm having problems getting my Iomega 160GB external hard drive to work.  It's A USB drive, and FAT23.  I don't think it's a compatibility issue, as it works fine with Ubuntu on my Asus EeePC and mounts automatically.

When I plug it in, I get an error saying "Cannot mount volume. Invalid mount option when attempting to mount the volume 'IOMEGA HDD'."

I got this output from cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2ffc3768-6020-4431-9682-b280c7c9520b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=629c6661-6a5f-494c-9c5d-ae61c5fa26bd /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D4-0A1B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=E4C89315C892E558 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=e2b2ff80-bc7b-4ded-9953-10b040352cf4 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec 0       0

```

And this from sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       18994   152497012+   7  HPFS/NTFS
/dev/sda3           18996       19452     3670852+  db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f05f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1459    11719386   83  Linux
/dev/sdb2            1460       30401   232476615    5  Extended
/dev/sdb5            1460       30158   230524686   83  Linux
/dev/sdb6           30159       30401     1951866   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd05371f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)

```

I'm still not very familiar with linux, or what this code means, so thought I'd better post this, before messing around with it!

Any ideas?

---

### Post by taurus on 2008-02-26
According to "sudo fdisk -l", your external harddrive is /dev/sdc1 but somehow you have an entry in /etc/fstab for /dev/sdc1 as a cdrom!  So, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and place a # in front of it to comment it out.

```
**[COLOR="Blue"]#[/COLOR]**/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
Save it and close down gedit window.  Now, run

```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
df -h
```

---

### Post by hj82 on 2008-02-26
Brilliant! It worked! Thanks...

---

