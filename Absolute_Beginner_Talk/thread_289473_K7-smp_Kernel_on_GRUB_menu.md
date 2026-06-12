---
title: "K7-smp Kernel on GRUB menu"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Yes_It's_Me on 2006-10-31
Hi folks, just installed edgy a few days ago and lovin' it, best release ever.

I am just fiddling around and started trying to install the k7-smp kernel for dual core processor (AMD Athlon 64 X2 4200+).

I am following this tutorial - [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917) I followed it reading everything and rebooted but my grub menu has no record of the k7-smp kernel, only "generic" and 386 that came with an update. I already have the restricted modules for my nvidia driver installed. Why is there no record on grub? Thanks is advance (and for all the other help you guys have given me, I am getting there!)

---

### Post by hopstah on 2006-10-31
the k7 and k7-smp kernels were replaced by the generic.  i don't know why, but that's what's going on.  so generic is the kernel you want to use.

---

### Post by Yes_It's_Me on 2006-10-31
> **hopstah said:**
> the k7 and k7-smp kernels were replaced by the generic.  i don't know why, but that's what's going on.  so generic is the kernel you want to use.

Thanks, I had the generic kernel right from the start and than the 386 came up after an update (i think) So with the generic kernel do I already have dual core support? So what should I do about the k7-smp kernel i installed, should I remove it?

Thanks again.

---

### Post by ubu_n00b69 on 2006-11-08
I used these to get my Dual Proc Intel PIII System up and running just 2 weeks ago.
It worked like a charm. Saw both procs without any Issues.
CPU 0 and CPU 1

-linux-image-2.6.12-9-k7-smp
-linux-image-k7-smp
-linux-restricted-modules-2.6.12-k7-smp
-linux-restricted-modules-k7-smp

Good Luck

---

