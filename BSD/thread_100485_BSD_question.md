---
title: "BSD question"
date: 2005-12-07
forum: BSD
---

### Post by PinkFloyd56 on 2005-12-07
I have XP and Ubuntu, I am going to install FreeBSD for a project I am doing and I need a more in depth view of the BSD port system. So during BSD installation will it detect grub is already installed, and there already is a swap drive so all I do is partition the hard drive I want?

-PF

---

### Post by baldy1324 on 2006-10-07
actually freebsd uses a completely different bootleader specific to freebsd. you can use the freebsd bootloader to handle all your os' or install freebsd in a seperate partition wo/ a bootloader and then enter your linux install and change grub/menu.lst to detect freebsd.

---

