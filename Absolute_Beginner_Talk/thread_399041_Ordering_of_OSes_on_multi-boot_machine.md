---
title: "Ordering of OSes on multi-boot machine"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Demeth on 2007-04-01
Is there a way to change the ordering on the first screen so that Windows is highlighted by default?

---

### Post by prensing on 2007-04-01
Well, you are not being very specific, but here is probably what you need. 

You probably mean the GRUB boot loader screen. The configuration is in /boot/grub/menu.lst. The line "default x" controls the default OS selected. Change the number; remember they are numbered starting with 0. 

Alternately, you can go in and rearrange the OS listings if you really want the menu in a different order.

---

### Post by royal314 on 2007-04-01
sort of related: why are thre 4 different choices of ubuntu on my grub screen?

---

### Post by oilchangeguy on 2007-04-01
probably due to a kernel update.

---

