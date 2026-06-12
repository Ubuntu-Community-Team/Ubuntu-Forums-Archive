---
title: "Lixux in window on G5?"
date: 2006-06-03
forum: Apple PPC Users
---

### Post by dpny on 2006-06-03
The G3 laptop I was using to run Linux finally died, leaving me with one machine. As it's my main machine I don't want to reformat or repartition it. Does anyone know of a way I can run Ubuntu in a Window, or on its own virtual desktop, on a G5? Parallels workstation looked promising, but it requires an Intel CPU.

I'm open to all suggestions.

---

### Post by digs on 2006-06-03
There was Mac-on-Mac but it no longer is being developed and doesn't work with the latest OS X. Your remaining choices are resizing your partition with VolumeWorks or Drive Genius or install on new hard drive (ppc macs can bootup from firewire). There is also a guide to resizing your partition via linux tools available in these forums - try a search.

---

### Post by EuroCity on 2006-06-03
... So, the only remaining option to run Linux in a window on a G5, besides Microsoft Virtual PC (a commercial product), would be the free, Qemu-based [Q](http://www.kberg.ch/q) emulator: of course, with an x86 Linux version as the guest OS, as PPC emulation sadly only works for the old 2.4 kernels.

The problem with emulation is that it is way too slow to be really usable: in particular, Qemu is very, very slow, at least on a G4; maybe it could be a little faster on a G5, anyway.

The best option, thus, always remains traditional dual-booting, or even running Mac OS X from within Linux, via Mac-on-Linux (MOL), as someone said previously.

---

### Post by dpny on 2006-06-05
[QUOTE=EuroCity]... So, the only remaining option to run Linux in a window on a G5, besides Microsoft Virtual PC (a commercial product), would be the free, Qemu-based [Q](http://www.kberg.ch/q) emulator: of course, with an x86 Linux version as the guest OS, as PPC emulation sadly only works for the old 2.4 kernels.

The problem with emulation is that it is way too slow to be really usable: in particular, Qemu is very, very slow, at least on a G4; maybe it could be a little faster on a G5, anyway.

The best option, thus, always remains traditional dual-booting, or even running Mac OS X from within Linux, via Mac-on-Linux (MOL), as someone said previously.[/QUOTE]

I found Q, installed it emulating x86 and was able to install 6.06 on it. It is, as you said, slow, slow, slow. . . However, Dapper installed, and it was funny seeing the Ubuntu boot screen in the middle of my OS X desktop. I'm hoping the Q PPC virtual machine abilities on the way (marked as Developer Only right now) arrive soonish.

I have Virtual PC. I wonder if it would be faster than QEMU.

---

### Post by EuroCity on 2006-06-05
Yes, Virtual PC is faster (sometimes much faster) than QEMU, at the current state of things on OS X: but it doesn't support 24-bit colour, so one must change the Xorg settings before being able to use Ubuntu (see also [http://vpc.visualwin.com](http://vpc.visualwin.com) for explanations on how to do this); also, remember to use Virtual Switch networking on a Linux guest, as shared networking sometimes doesn't work.

BTW, here is a screenshot I made some days ago, only as a temporary experiment to see how well Dapper worked in VPC (it is indeed quite slooooow, especially to install, but certainly more usable than Q!):

[[IMG]http://idisk.mac.com/eurocity/Public/UbuntuVPCa.png[/IMG]](http://idisk.mac.com/eurocity/Public/UbuntuVPC.png)

(click to enlarge).

---

### Post by dpny on 2006-06-05
> **EuroCity]Yes, Virtual PC is faster (sometimes much faster) than QEMU, at the current state of things on OS X: but it doesn't support 24-bit colour, so one must change the Xorg settings before being able to use Ubuntu (see also [http://vpc.visualwin.com](http://vpc.visualwin.com) for explanations on how to do this) said:**
> [IMG]http://idisk.mac.com/eurocity/Public/UbuntuVPCa.png[/IMG][/URL]

(click to enlarge).

Thanks for the info. I will try and install 6.06 on VPC this weekend if I have the time.

---

### Post by dpny on 2006-06-11
Got it up and running: 

[IMG]http://img.photobucket.com/albums/v292/noewun/Ubuntu_VPC_2.jpg[/IMG]

It's slow, but faster than Q. I can use it to screw around with, but it's too slow for real work. If I had a dual processor machine, it might be fast enough to use.

---

