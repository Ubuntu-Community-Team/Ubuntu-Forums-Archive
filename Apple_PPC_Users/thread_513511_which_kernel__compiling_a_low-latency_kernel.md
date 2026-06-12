---
title: "which kernel // compiling a low-latency kernel"
date: 2007-07-30
forum: Apple PPC Users
---

### Post by jaskah on 2007-07-30
ok, so i finally got my sound working again on my g4 titanium by using linux-image-2.6.17-12-powerpc_2.6.17.1-12.39_powerpc.deb (but only with my rme hammerfall, system sound is still not working...) .
now, i would like to compile this same kernel for low-latency.
**my question: **on the kernel.org site i am not sure which of the several 2.6.17-12 kernels to download
[ftp://ftp.kernel.org/pub/linux/kernel/v2.6/](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/)
i tried compiling the linux-2.6.17.12.tar.bz2 kernel but ran into problems at the end; not sure if this kernel is complete.
thanks for any help!

---

### Post by stmiller on 2007-07-31
You can recompile that provided Ubuntu kernel, or fetch this one:

[ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.19.7.tar.bz2](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.19.7.tar.bz2)

to compile on your own. (The last kernel before 2.6.20.x) There are methods for compiling a kernel and enabling low latency and such in the PowerPCFAQs - link in my profile or at the sticky at the top of the page.

Make sure to put

snd-powermac
snd-seq

at the end of the file

/etc/modules

also, so the modules are loaded at boot. Good luck!

---

### Post by jaskah on 2007-07-31
thanks for your help! great.
i actually know your tutorial about compiling a low-latency kernel (very helpful)--for some reason it didn´t work with the linux-2.6.17.12.tar.bz2 kernel.
but i will go ahead and try with the [ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.19.7.tar.bz2](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.19.7.tar.bz2)
like you suggested.
and thanks for the tip with changing /etc/modules. now on-board mac sound works fine.

---

