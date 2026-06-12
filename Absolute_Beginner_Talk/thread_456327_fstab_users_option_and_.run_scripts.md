---
title: "fstab users option and .run scripts"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by srg84 on 2007-05-27
Hi, why when I mount my partition with the "users" option (to be able to mount it with Nautilus), I can't install Ati drivers for example because it says that:

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

Anyone?

---

### Post by yabbadabbadont on 2007-05-27
If you are trying to run an installation script off of the partition that you mounted with "users", it may be that it is also mounted with the "noexec" option that prevents programs/scripts from being executed.  In a terminal, run "mount" and see which options were used when the partition was mounted.  If "noexec" is listed, you may have to modify your /etc/fstab so that that partition's entry includes "exec" in it's mount options.

---

