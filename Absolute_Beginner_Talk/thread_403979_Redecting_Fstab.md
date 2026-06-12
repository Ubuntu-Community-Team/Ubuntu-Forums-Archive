---
title: "Redecting Fstab"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-04-07
After changing around some partitions, the uuid's for them in fstab have changed. Is there any way to have Ubuntu automatically redetect the changes, or must it be done manually?

---

### Post by bruenig on 2007-04-07
Probably need to do it manually.

---

### Post by freebird54 on 2007-04-07
You could try this for manual use:

```
sudo fdisk -l
```

to get a list of the partitions.  And then this:

```
sudo vol_id /dev/***partname***
```

where ***partname***=hda1 or sda2 or whatever you need ( from the list you generated with the first command)

Hope it helps!

---

