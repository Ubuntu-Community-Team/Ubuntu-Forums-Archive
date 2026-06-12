---
title: "how to roll back a kernel?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by lopagof on 2007-06-04
how can I change back to an older kernel version on xubuntu 6.10?

---

### Post by pbw on 2007-06-04
If you haven't cleaned your cache, take a peek in /var/cache/apt/archives for the version you want and enter sudo dpkg -i /var/cache/apt/archives/kernelapackage.deb. 

Also, if you didn't uninstall the old kernel, it should still be on your system. Just look at /boot/grub/menu.lst and switch which kernel boots default.

---

