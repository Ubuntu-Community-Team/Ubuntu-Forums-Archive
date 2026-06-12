---
title: "Installing on External USB HD?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-07-02
I have a 160gb Toshiba External USB Hard Drive , 55gb of which is an ext3 partition with very little sitting on it. Would it be possible to install another distro (or two) onto that partition (obviously split it into two if i was installing two distros) and then boot it from my Fedora 7 Grub list?

---

### Post by aquavitae on 2007-07-02
You won't be able to install it onto the ext3 unless you remove everything on it first, but you can resize the partition and use the space created to install new distros.  Then just edit /boot/grub/menu.lst to add them to the boot menu.  Btw, make sure you don't reinstall grub when you install the new distros.

---

