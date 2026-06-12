---
title: "Triple Boot Help [Freedos, WinXP, Ubuntu 6.06"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Phototrek1 on 2006-09-08
Hi, I just got ubuntu and i like the os alot. However i want to triple boot my laptop. Ubuntu and Windows work together great. But when i added the Freedos Partition Using Xfdisk.com. Neither OS seen the partition. I want to be able to move my dos games/apps to the freedos partition and use Dosbox in both windows and Ubuntu and then boot from it.

Thanks,:-k

---

### Post by derjames on 2006-09-27
I am succesfully running DOOM under Ubuntu 6.06 using QEMU+FreeDOS
using QEMU as a virtual machine and FreeDOS as the guest OS, DOOM runs perfectly and is quite fast despite de emulation (I haven't tried wine, though)
QEMU and FreeDOS are available from Synaptic, however the FreeDOS version is the 0.8, I did download FreeDOS 1.0 from the FreeDOS.org website... The installation is pretty straightforward but you need to tell QEMU to create a VFAT virtual drive (apart from the virtual drive created for the FreeDOS installation) just to exchange data between LINUX y FreeDOS.

Cheers

---

