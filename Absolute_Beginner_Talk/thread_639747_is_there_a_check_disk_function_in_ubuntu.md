---
title: "is there a check disk function in ubuntu?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by tysonh on 2007-12-13
I have a few bad sectors on my hard drive accounting to ubuntu.  How do I find them and repair them.  I looked at some other threads about it.

I tried umounting the hard drive and running the file check but it said it wasn't mounted.
I tried it a different way and it said it was mounted.  I'm a lost on how to proceed.

---

### Post by Bert_2 on 2007-12-13
If you mean that there are bad sectors in the ubuntu partitions ?
Normally if it is ext3 that will be fixed after 38 mounts or 3 months if I remember right, it happens when you boot your system and goes so fast that you don't even notice it.

---

### Post by TheLions on 2007-12-13
run partition editor (if you don't have it you can get it from programs-->add/remove programs and then type "gnome partition editor")

choose partition and press partition-->check

:)

---

### Post by asmoore82 on 2007-12-13
the `badblocks` utility will detect sectors that are physically bad;
However, these are not repairable and if any are found, you should back up
all of your important data on a different drive and replace that one ASAP.

---

### Post by philinux on 2007-12-13
> **tysonh said:**
> I have a few bad sectors on my hard drive accounting to ubuntu.  How do I find them and repair them.  I looked at some other threads about it.

I tried umounting the hard drive and running the file check but it said it wasn't mounted.
I tried it a different way and it said it was mounted.  I'm a lost on how to proceed.

fsck is the filesystem check that will run every so many boots depending on the file systems size, usually around 36.

Can you post the errors that are being reported - is this at boot up - is it preventing the system from running?

---

### Post by tysonh on 2008-06-18
thanks for the help

---

