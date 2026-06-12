---
title: "Mounting Windows Partition wont work."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by denysy1 on 2007-04-12
Hi,

I am trying to mount my windows partition, so I followed this guide here: 

[http://www.arsgeek.com/?p=675](http://www.arsgeek.com/?p=675)

I followed each step closely and did not get any errors.

Here is what "sudo fdisk -l" gave me:
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8430    67713943+   7  HPFS/NTFS
/dev/sda2            8431       12005    28716187+  83  Linux
/dev/sda3           12006       12161     1253070    5  Extended
/dev/sda5           12006       12161     1253038+  82  Linux swap / Solaris

```

This is how my fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=97ef8682-ee5d-465b-b26e-32eaa30b9cf1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4c6e21ca-0b6d-4914-ac01-19493a0677c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

```

Did I make some mistake? Could anyone suggest a better guide to mounting windows partitions?

---

### Post by taurus on 2007-04-12
Do you have /media/windows?

```
ls -la /media
```
If not, create it so /dev/sda1 can mount to it.

```
sudo mkdir /media/windows
sudo mount -a
df -h
```

---

### Post by denysy1 on 2007-04-12
OK never mind, I had it all along:o , just didnt find it. I expected an icon to appear on the desktop.... oh well, stupid me:( . Thanks.

---

