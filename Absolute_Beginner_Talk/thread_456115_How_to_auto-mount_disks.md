---
title: "How to auto-mount disks?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ChrisCummins on 2007-05-27
**EDIT: This has now been resolved.**

Hiya, quick question: how do you get a disk to mount automatically on startup?

Chris

---

### Post by taurus on 2007-05-27
Just add an entry in /etc/fstab.  Which partition do you want to mount automatically upon boot?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ChrisCummins on 2007-05-27
The disk is /dev/hdb1, named "disk".

>    Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       11497    92349621   83  Linux
/dev/hdb2           11785       12161     3028252+   5  Extended
/dev/hdb5           11785       12161     3028221   83  LinuxAt the moment, here's what my fstab looks like:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=57fd24ea-5101-4a5e-abf9-33f023e81d02 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1339daeb-047f-4fa4-8e1a-9fc118c7ab4e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I'm not sure what the additional entry would like. While I'm at it, could I remove the 'floppy0' entry, as I'm not sure what it is but I don't have a floppy drive installed!

Thanks for the help!
Chris

---

### Post by taurus on 2007-05-27
Okay, I assume you want to mount both /dev/hdb1 & /dev/hdb5.  Open a terminal and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two entried to the end of it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
/dev/hdb5   /media/hdb5   ext3   defaults   0   1
```
You can also place a # in front of an entry for your floppy to comment it out.

Save the changes and then create two new mount points for them.

```
sudo mkdir /media/hdb1 media/hdb5
```
Reboot and you should be both /dev/hdb1 & /dev/hdb5 mount to /media/hdb1 & /media/hdb5, respectively.

```
df -h
```

---

### Post by ChrisCummins on 2007-05-27
Cheers mate, that's excellent! :)

---

