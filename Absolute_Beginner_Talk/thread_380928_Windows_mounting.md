---
title: "Windows mounting"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by natman on 2007-03-10
On my old computer when i installed ubuntu it gave me the option of seeing the windows hard drive when i clicked on storgae media, i could copy files and look around.
On my new latop with 6.10 ( 64 bit ) i can 84GB media, i click and then "unknow error" can i have it so that its always there to look around in?

Thanks:

---

### Post by Obor on 2007-03-10
What does you fstab look like?
```
gedit /etc/fstab
``` or ```
kate /etc/fstab
``` if you are in kubuntu

And your partition table?
```
sudo fdisk -l
```

Do you want to write into your windows partition or just read?

---

### Post by natman on 2007-03-10
ftab is 
[HTML]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1d9abb65-f943-488f-b9fc-ade4156817d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e7014e8a-2357-4b8c-9882-bd52527a68c4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

[/HTML]

and fdisk-l

[HTML]
isk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10248    82317028+   7  HPFS/NTFS
/dev/sda2           18771       19097     2626627+   f  W95 Ext'd (LBA)
/dev/sda3           10249       18770    68452965   83  Linux
/dev/sda5           18771       19097     2626596   82  Linux swap / Solaris

Partition table entries are not in disk order
natman@natman-laptop:~$

[/HTML]

---

### Post by taurus on 2007-03-10
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```

---

