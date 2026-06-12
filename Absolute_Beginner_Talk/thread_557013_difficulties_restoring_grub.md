---
title: "difficulties restoring grub"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by denver38 on 2007-09-22
I have WindowsXP, Ubuntu and Kubuntu installed.
I wanted to delete the Ubuntu partition using **fixmbr **, but this deleted/disabled the grub boot loader.
I have an alternative (texmode) livecd so I entered in my kubuntu partition, opened a shell and I typed grub (to reinstall grub).
this gave the following error
Error opening terminal: bterm

Any suggestions?

---

### Post by alienexplorers on 2007-09-22
First off it is
> sudo grub
you can then follow the directions in my sig line for reloading Grub.

---

### Post by denver38 on 2007-09-22
thanks for your quick reply, but I already tried sudo grub and the same error message returns.
I'm going to try it again with the livecd instead of the alternative one...

---

### Post by denver38 on 2007-09-23
thanks, I managed to fix it
grub wasn't recognizing the drive so your topic was very clear and useful

---

