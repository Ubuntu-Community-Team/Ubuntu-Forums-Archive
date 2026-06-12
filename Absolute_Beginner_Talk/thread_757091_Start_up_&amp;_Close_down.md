---
title: "Start up &amp; Close down"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by centeur on 2008-04-16
Hi All. Recently installed Ubuntu 7.10. Find that it takes 3.5 mins to load and to turn it off I have to press the start button on the PC. Can anyone help please?

---

### Post by ace007 on 2008-04-16
Could you post your computer's specs as a first step?

CPU:
RAM:
GRAPHICS:

---

### Post by spiderbatdad on 2008-04-16
Probably a hardware detection problem. I went from a 4-5 minutes boot time to around 32 seconds by adding lapic to the kernel line in /boot/grub/menu.lst, running dpkg-reconfigure xserver-xorg, updating initramfs, and doing a one time profile of the boot process.

Reading dmesg should tell you if you need to add lapic to the kernel line.

---

