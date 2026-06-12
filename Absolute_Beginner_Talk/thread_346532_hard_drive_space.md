---
title: "hard drive space"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by pesach on 2007-01-25
How do I know how much space is left on my hard drive?
I right clicked on the hard drive icon under "computer" but ubuntu for some erason was not able to recognize it.  WHen I did a sudo fdisk -l it gave the right hard drive size, partitions and everything, but I didnt really see anywhere where it told me how much space was actually left.  Here is what I got:
```
Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2392    19213708+  83  Linux
/dev/hda2            2393        2498      851445    5  Extended
/dev/hda5            2393        2498      851413+  82  Linux swap / Solaris
```

---

### Post by aysiu on 2007-01-25
```
df -h
``` should help.

---

### Post by DSn0wMan on 2007-01-25
Try this:
```
 df -h
```

---

### Post by pesach on 2007-01-25
Thank you! edit- (and thats why I love ubuntu so much- two answers in under four minutes!)

---

### Post by pesach on 2007-02-11
talking about hard drive space, for some reason about 5 gb of space is being used on my hard drive were the only thing on it is the ubuntu os.  no pics, no movies, no nothing.  Is the operating sysstem reallyl tat big?

---

