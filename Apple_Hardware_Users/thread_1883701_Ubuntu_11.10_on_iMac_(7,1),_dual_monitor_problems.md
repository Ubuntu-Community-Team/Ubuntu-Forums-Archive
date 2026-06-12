---
title: "Ubuntu 11.10 on iMac (7,1), dual monitor problems"
date: 2011-11-19
forum: Apple Hardware Users
---

### Post by mhubas on 2011-11-19
Hi,

I'm trying to install Ubuntu 11.10 (64-bit) on my iMac (7,1) on it's own partition (triple boot with rEFIt installed), but I'm having dual monitor problems. During installation (and also after installation), only the external monitor was working. The iMac monitor was detected, but was not displaying anything. After researching about the problem, I tried booting with the "nomodeset" option, which solved the problem. Then, when I tried to install the Additional Drivers (AMD FGLRX Drivers), the same problem came back, but this time I'm not able to fix it...

What I find confusing is that Ubuntu 11.10 (and the Additional Drivers) worked like a charm when I installed it with Wubi on the exact same machine.

Does anyone have the same problem? Does anyone know what I could verify or try to fix the problem?

Thank you!

---

### Post by mhubas on 2011-12-04
It seems it was related to the way I installed Ubuntu 11.10 (64-bit) on  my iMac. I could boot the installation CD in EFI mode or in BIOS mode,  but the BIOS mode wasn't booting, so I installed it in EFI mode without  really being aware of it. Finally, I noticed that the EFI mode  installation was the cause of my dual screen problems and I found two  solutions.

The first solution is to download an image from [http://cdimage.ubuntu.com/releases/oneiric/release/](http://cdimage.ubuntu.com/releases/oneiric/release/). For example, "ubuntu-11.10-desktop-amd64+mac.iso" should work, but I did not try it myself.

The second solution is to install it with the official image in EFI mode  (like I already did), to create a partition with the "bios_grub" flag  and to install the "grub-pc" package afterwards.

---

