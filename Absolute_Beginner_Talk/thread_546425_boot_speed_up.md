---
title: "boot speed up"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by fazillatheef on 2007-09-08
hi
How can I turn off dosfsck which runs in the startup .

---

### Post by kerry_s on 2007-09-08
there is no "dosfsck", there's fsck, thats to make sure your system files are okay.

i don't recommend turning it off, but if you must.
alt+f2
gksudo gedit /etc/default/rcS

FSCKFIX=no
to
FSCKFIX=yes

---

