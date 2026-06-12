---
title: "Drivers"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Reddoug on 2007-12-04
Hi all

Being very new to Ubuntu and I have ver 7.10 installed on an older computer,450Mhz with 320 mb of ram,  were can I find drivers for an old 3com ISA network card? I just joined this group. 

Thanks,  Reddoug

---

### Post by PeterJS on 2007-12-04
> **Reddoug said:**
> Hi all

Being very new to Ubuntu and I have ver 7.10 installed on an older computer,450Mhz with 320 mb of ram,  were can I find drivers for an old 3com ISA network card? I just joined this group. 

Thanks,  Reddoug


Kinda of a silly question given that you're asking about drivers, but is it working? All of the drivers in linux are modules of the kernel itself, I can't imagine that something that old had drivers written for it that didn't end up in the main kernel by now. Ubuntu is generally pretty good about building every module, and loading them.

If it isn't loading can you post the output of running lspci (list pci, I hope it lists the ISA bus too, never had to worry about that before) on that machine?

---

