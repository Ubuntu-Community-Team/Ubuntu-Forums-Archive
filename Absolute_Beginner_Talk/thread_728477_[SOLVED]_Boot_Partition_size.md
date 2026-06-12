---
title: "[SOLVED] Boot Partition size"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2008-03-18
hey all,

what is the minimum size of the /boot partition (ie can I fit it on an 32MB CF card). Ill have the core / partition somwhere else of course


thanks in advance

---

### Post by AmyRose on 2008-03-18
It should work, but putting your /boot partition on a CF card isn't necessary in most cases, especially if your computer can boot from them. The purpose of the /boot partition is mainly to allow you to force the boot files to be within the first 2 or 8 GB of the disk so you can use a large hard drive in an old computer without installing any additional drivers.

---

### Post by Slingshot on 2008-03-18
There is a recommended size for partition somewhere in the support documents. Just looking at my /boot partition is using 25mb.

---

### Post by JasonBourneLinux on 2008-03-18
alright- thanks for the help guys! (I am using an older comp that cant boot via USB and such- Im taking advantage of one of those CF to IDE adapters and a stock 32 MB unused CF card that came with my brother's Canon camera)

---

