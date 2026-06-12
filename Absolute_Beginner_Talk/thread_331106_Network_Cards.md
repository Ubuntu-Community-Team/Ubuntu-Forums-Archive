---
title: "Network Cards"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Brian R. on 2007-01-04
Installed ubuntu some weeks ago, and have now added a Network card (Realtek8139).
The system in hardware devices, but how do i access it.  It comes with drivers for SCO Linux, or does ubuntu have the drivers on the CD, if so how do i install them. Then how do i activate them.

---

### Post by kidders on 2007-01-04
Hi there,

I *think* the kernel module for your network card is called "8139too". It should load automatically if suitable hardware is detected, unless you intentionally blacklisted it. (I have memories of using that module in the past.)

Check **lsmod|grep 8139** to see if it's been loaded already. If not, you could try loading it manually ... assuming, of course, I'm right about the module name!

---

