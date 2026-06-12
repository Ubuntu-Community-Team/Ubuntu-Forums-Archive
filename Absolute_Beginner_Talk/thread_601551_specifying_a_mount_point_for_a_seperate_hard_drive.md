---
title: "specifying a mount point for a seperate hard drive"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by myk.dinis on 2007-11-03
How do I specify a persistent mount point for say hdd1?

I have it done for another drive but I had to do it at the time of installation...

I want to be able to do it now...

And when I use gparted it doesn't give me any mount point options...


Any ideas?

Thanks

Myk

---

### Post by geforce123 on 2007-11-03
The mount points table is

/etc/fstab

In this file you can modify it.

---

### Post by taurus on 2007-11-03
What filesystem is /dev/hdd1?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by myk.dinis on 2007-11-03
ext3...At least that's what I formatted it to and that's what gparted now reports...

---

### Post by myk.dinis on 2007-11-03
geforce --

I added a line to my fstab to try and overcome that problem but I then checked in my mtab and it didn't report the drive...
taurus--
Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4866    39086113+  83  Linux


blah...

---

### Post by geforce123 on 2007-11-10
Can you post the line you inserted in /etc/fstab ?

If it's not the problem, could it be a dying hard drive ?

You can also try to re-write the partitions table.

(make sure the drive is unmounted)
fdisk /dev/hdd
press w and [enter]
try to mount it again ..

---

