---
title: "unmounting windows partion"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-10-26
I need help

---

### Post by Crafty Kisses on 2007-10-26
> **LiNuXxToOthEMaX said:**
> I need help

Well, to unmount the partition simply just go into terminal and enter the following:
```
sudo umount /media/hda1
```

---

### Post by MegaJim on 2007-10-26
you know how to use a terminal?

```
sudo fdisk -l
```

find your windows partition in that list.  make sure no programs are accessing it, then

```
sudo umount /dev/???
```

where ??? is the drive identifier, (e.g. /dev/hda1 or /dev/hdb3)

---

### Post by LiNuXxToOthEMaX on 2007-10-26
> **Codename said:**
> Well, to unmount the partition simply just go into terminal and enter the following:
```
sudo umount /media/hda1
```

how do i view it or look at it or w/e

---

### Post by Crafty Kisses on 2007-10-26
> **LiNuXxToOthEMaX said:**
> how do i view it or look at it or w/e

Not sure what you're asking, but try this:
```
sudo fdisk -l
```

---

### Post by arpanaut on 2007-10-26
If you would please elaborate on your problem and what you need help for it would go a long way towards getting assistance.

:confused:

---

### Post by Crafty Kisses on 2007-10-26
> **arpanaut said:**
> If you would please elaborate on your problem and what you need help for it would go a long way towards getting assistance.

:confused:

I was a little confused, but I think his problem is solved. Please let us know. :)

---

