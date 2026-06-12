---
title: "Uninstalling kernel"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by BrandNuUbantu on 2006-05-07
Hi all,
How do i uninstall the old kernels?

TIA
BNU

---

### Post by hw-tph on 2006-05-07
**sudo apt-get remove --purge <kernel-image>**
...like so: **sudo apt-get remove --purge kernel-image-2.6.16-ck6**

Always keep a backup though.


Håkan

---

### Post by AnRuaRi on 2006-05-07
Personally I prefere to use Synaptic. It's a graphical front end for apt-get, but it lets you see what's installed or available for upgrade, along with discriptions of the packages.

---

