---
title: "How do I mount a ext3 partion?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2007-03-10
I have two installs of ubuntu on my hardisk and I want to transfer stuff from one to the other. How do I mount the other one.

my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9be9cd3d-cf19-4c19-9553-4fcc7977d406 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=a095d89d-5261-4939-81b4-5da2cc67d426 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by happy-and-lost on 2007-03-10
> You want to mount hda*x*, yes? Type the following into the console:

sudo mkdir /media/hda*x*
sudo mount /dev/hda4 /media/hda*x*

Sorry. Misread that. I can't see the other install there. Which partition is it on (hda...?)?

---

### Post by Iarwain ben-adar on 2007-03-10
Hi there,

it's quite easy actually:
```
mkdir ~/other_ubuntu_partition
sudo mount /dev/hdaX ~/other_ubuntu_partition
```

To know what X it is, 

```
sudo fdisk -l
```

This should work :D

Or do you want to add it to your fstab?


Iarwain

---

### Post by george29 on 2007-03-10
from your fstab /dev/hda4 is the swap partition...

you need to find out what partitions you have so 

```
sudo fdisk -l
```
to list the partitions on your hard drive

then when you have identified the partion you want probaby hda2 or hda3 follow the instructions happy-and-lost posted

---

