---
title: "[SOLVED] mutiboot"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-02-01
OK you have convinced me to only install one ubuntu kernel and use KDE, and Xfce through ubuntu. But what about fedora? If ubuntu installs grub but doesn't delete my windows boot loader, will fedora do something like that also? In other words, how do I try any other operating system after grub is already installed? Or will I have to reinstall ubuntu after installing other op systems?

---

### Post by bodhi.zazen on 2007-02-01
> **rusty4r said:**
> OK you have convinced me to only install one ubuntu kernel and use KDE, and Xfce through ubuntu. But what about fedora? If ubuntu installs grub but doesn't delete my windows boot loader, will fedora do something like that also? In other words, how do I try any other operating system after grub is already installed? Or will I have to reinstall ubuntu after installing other op systems?

In general, when you install Linux (Ubuntu or Fedora) GRUB will be updated to include all OS at the time of install.

It can become a bit more complicated as you maintain ... You may need to update /boot/grub/menu.lst manually or use chainloader ...

See here for a complete guide [How to GRUB](http://users.bigpond.net.au/hermanzone/p15.htm)

Ask if you have further, specific questions ...

---

### Post by rusty4r on 2007-02-01
> **bodhi.zazen said:**
> In general, when you install Linux (Ubuntu or Fedora) GRUB will be updated to include all OS at the time of install.

It can become a bit more complicated as you maintain ... You may need to update /boot/grub/menu.lst manually or use chainloader ...

See here for a complete guide [How to GRUB](http://users.bigpond.net.au/hermanzone/p15.htm)

Ask if you have further, specific questions ...

Awesome link, thank you very much

---

