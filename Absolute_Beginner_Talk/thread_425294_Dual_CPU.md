---
title: "Dual CPU"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-04-27
How do you go if you have a PC with two P3 667Mhz CPUs on the M.B.?
If I install Ubuntu 6.06 from the disc I used for my other PC will it work with the two CPU's?

---

### Post by rufius on 2007-04-27
Yes it will work. The installer will setup an smp kernel. SMP is Symmetric Multi-Processing, which is means having more than one logical processing unit. Should work fine out of box.

---

### Post by Cypher on 2007-04-27
The Linux Kernel employs a mechanism known as SMP (Symmetric Multi-Processing) that makes use of 2 or more CPU's. Back in the day, this worked with 2 physical CPUs, and these days it work with multi-core CPUs just the same..

So if you install from the disc, you can run "uname -a" in the Terminal after installation and see if it says SMP on there..

---

