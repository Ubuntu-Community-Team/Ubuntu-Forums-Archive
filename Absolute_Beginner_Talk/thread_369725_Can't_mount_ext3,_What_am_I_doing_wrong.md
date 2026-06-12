---
title: "Can't mount ext3, What am I doing wrong?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by C-A on 2007-02-24
I am trying to mount this partition:

> Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7476    60050938+  83  Linux

By running this command after creating this directory "/media/max60a":

> sudo mount /dev/hdd1 /media/max60a/ ext3 defaults 0 1

And this is my output:

> Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


What am I doing wrong?

---

### Post by taurus on 2007-02-24
```
sudo mount -t ext3 /dev/hdd1 /media/max60a
```

---

### Post by C-A on 2007-02-24
> **taurus said:**
> ```
sudo mount -t ext3 /dev/hdd1 /media/max60a
```

Bingo, thanks!

---

