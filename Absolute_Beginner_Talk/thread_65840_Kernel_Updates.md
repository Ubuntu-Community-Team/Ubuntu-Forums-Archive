---
title: "Kernel Updates"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by cnayak on 2005-09-15
What are the advantage of upgrading the linux kernel? Obviously, newer kernels should be better , but do they bring any new features? Currently, I have the 2.10 - 5 kernel and my system is pretty stable and every peice of hardware is detected (except the battery charege meter :( ). So, Should I go for the latest 2.13 kernel?

---

### Post by heimo on 2005-09-15
There are many reasons for kernel updates. Every kernel version change means hundreds of small changes, bug fixes, added modules (drivers, new hardware support). These changes are listed in ChangeLogs (quite hard to read if you don't know what you're looking for) available at [http://www.kernel.org/](http://www.kernel.org/) Sometimes there are also security fixes and that's a very good reason to upgrade.

Most of the time upgrade to new stable kernel does not cause any problems, and you can have several versions of kernel installed, so you can easily change back to older one if any problems would occur (this is done in grub menu, accessible at beginning of boot by hitting ESC).

You may also want to check that you have the best available kernel for your processor. You can open a terminal window Applications->System Tools->Terminal or alt+F2, write xterm and hit Run. In terminal, type *uname -r *This tells you the kernel you're currently using. If you have Pentium processor, you should install 686 version (386 is the default), and K7 for most AMD processors. However I'm using 686 on my Athlon XP and it works just fine. Reason for these different versions is optimization - different processors have different extensions (capabilities). Also 386 kernel supports "only" around 850MB memory.

---

