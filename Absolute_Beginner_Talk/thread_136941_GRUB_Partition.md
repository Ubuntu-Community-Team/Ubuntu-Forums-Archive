---
title: "GRUB Partition"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-02-27
I want to make a seperate partition for GRUB. What size should it be?

Don Cole

---

### Post by Sutekh on 2006-02-27
You could make a boot partition mounted at /boot.  GRUB lives in /boot/grub. 

GRUB itself is quite small, but kernel images are put in /boot, so it needs to be big enough for all of them that you may use.  I think 100~150MB should be okay.

---

