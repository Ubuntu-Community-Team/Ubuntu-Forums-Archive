---
title: "problem with permissions and a new HD."
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by timmins on 2006-10-17
HI,i used the search functions but couldn't find what I was looking for.:

I have my newly formatted (fat 32) IDE HD hooked up and mounted.

When I try to make the HD writable in the permissions tab, it says: "The permissions could not be changed. sorry, couldn't change the permissions of "149.0 GB volume:ide disk".

how do I access this Hd in the terminal and change the permissions?

Thanks

---

### Post by timmins on 2006-10-17
[https://help.ubuntu.com/community/VolumePermissions?highlight=%28permissions%29](https://help.ubuntu.com/community/VolumePermissions?highlight=%28permissions%29)

Is this what I need?

---

### Post by aysiu on 2006-10-17
Try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by timmins on 2006-10-17
as per the site you linked, i followed the forst instruction and hit a snag. please tell me exactly what to write, since the language used in the terminal is still not clear. BTW the HD is fat 32.

sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
kyle@ubuntu:~$

Thanks

---

### Post by aysiu on 2006-10-17
It's not a 1. It's an l--that's a lowercase L, not the number 1 or an uppercase i.

---

### Post by anaconda on 2006-10-17
You could propably write to it as root user:

in terminal type:
gksudo nautilus
to open file browser with root rights.

But maybe it isn't a good idea to use root rights if not really needed..

---

### Post by timmins on 2006-10-17
kyle@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris
kyle@ubuntu:~$ sudo mkdir/windows
sudo: mkdir/windows: command not found
kyle@ubuntu:~$


what did i do now

---

### Post by aysiu on 2006-10-17
You need a space between *mkdir* and */windows*.

**No space**: ```
sudo mkdir/windows
``` **Space**: ```
sudo mkdir /windows
```

---

### Post by timmins on 2006-10-17
thanks aysui, I need glasses, I have trouble reading the screen.
now my screen lloks different than the one pictured, what do I do.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by aysiu on 2006-10-17
By the way it's always simplest to copy and paste commands into the terminal instead of retyping them.

Hm.

I didn't see a FAT32 drive in your *sudo fdisk -l* output. Is the drive physically plugged in? The first drive appears to be NTFS. The second drive appears to be Ext3 (Ubuntu's filesystem).

---

