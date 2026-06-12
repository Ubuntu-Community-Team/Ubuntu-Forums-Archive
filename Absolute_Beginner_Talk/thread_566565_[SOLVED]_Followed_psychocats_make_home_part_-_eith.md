---
title: "[SOLVED] Followed psychocats make home part - either partition locked or resize greye"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-03
Tried live ubuntu cd way too slow and partitions locked.
In knoppix live cd now and qtparted resize option is greyed out.
I've change hda1 to read write. What am I missing.

---

### Post by jordanmthomas on 2007-10-03
It needs to be unmounted before you can resize it.
```
mount -a
```
will list what's mounted.  If your partition you want to mess around with is mounted, you must unmount it:
```
umount /dev/hda1
``` for example

---

### Post by philinux on 2007-10-03
It is unmounted, but qtparted and gparted mount the drive

---

### Post by philinux on 2007-10-03
Here is a screenshot of qtparted.

I can resize the extended and swap partitions but not hda1. It also says hda1 is busy?

---

### Post by philinux on 2007-10-03
bumpty bump

---

### Post by philinux on 2007-10-04
Had to use Gparted cd both ubuntu7.04 and knoppix 5 must utilise theHD in some way.

---

