---
title: "Kernel question"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by philip.yhelzon on 2007-10-19
I have upgraded from 7.04 to 7.10
When I boot it gives me the choice between the new kernel and the old one.
when I boot with the old one everything works great (more or less).
When I boot with the new one everything is extremely buggy.

So...I guise my questions are:
why do I have both installed (with the old one as default)?
What is the big difference between the 2 Kernels?
Do I have to switch to the new one?



thanx.

---

### Post by Daveth on 2007-10-19
sometimes the differences between kernels are very much under the hood, and often not that obvious. They may be additions to give better support to hardware, or changes to libraries, or other additions. There are always changelogs associated with new kernel releases, which you can easily find on the web. You can use what version you want. Grub just keeps holds of them in its list at /boot/grub/menu.lst.

---

