---
title: "lost space on SSD"
date: 2013-05-01
forum: Any Other OS
---

### Post by robin 123 on 2013-05-01
Hi, I've been using Linux Mint (based on Ubuntu, that's why I am asking here) for over 2 months on a new Kingston 120GB SSD. I had done all the suggestions on various webpages for running a system on SSD and never had problems. But now I've noticed that there is 20GB less free space than there should be!

See the attached picture.
The disk is denomially 120GB, which translates to around 110GB.
The analyzer says there is 90,5GB occupied and 19,5GB free.
However the base folder has only 69,5GB altogether and there is no other attached partition on the disc! (Of which 62GB is my home folder and 7,5GB the system)
So where is the remaining 20GB?

Any ideas where it might have got lost? Could the disc be corrupted?

---

### Post by Perfect Storm on 2013-05-01
Moved to Other OS/Distro Support.

---

### Post by mips on 2013-05-02
post output of **sudo fdisk -l**

---

### Post by pqwoerituytrueiwoq on 2013-05-02
are you using trim?
[FONT=courier new]sudo fstrim /[/FONT]

---

