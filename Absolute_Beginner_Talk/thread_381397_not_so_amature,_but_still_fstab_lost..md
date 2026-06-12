---
title: "not so amature, but still fstab lost."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by puccaso on 2007-03-10
how do i make ubuntu auto-recreate an fstab file??

---

### Post by gradedcheese on 2007-03-10
No idea, but I can tell you how to manually create it...

First, run:

sudo fdisk -l

for example:

```

/dev/hda1   *           1        4662    37447483+  83  Linux
/dev/hda2            4663        4864     1622565    5  Extended
/dev/hda5            4663        4864     1622533+  82  Linux swap / Solaris

```

Tells me that I need /dev/hda1 as '/' in fstab, and /dev/hda5 as 'swap'.   A basic fstab can then be:

```

proc            /proc           proc    defaults                                   0  0
/dev/hda1  /                   ext3    defaults,errors=remount-ro  0 1
/dev/hda5  none           swap  sw                                             0 0

```

---

