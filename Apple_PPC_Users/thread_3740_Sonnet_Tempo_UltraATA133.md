---
title: "Sonnet Tempo UltraATA133?"
date: 2004-11-09
forum: Apple PPC Users
---

### Post by regeya on 2004-11-09
Anyone have any luck installing Ubuntu on a machine using one of these cards?  I have a machine we use as a fileserver, an older Gigabit Ethernet G4 with a Sonnet Tempo UltraATA 133 card, a couple of 250GB WD drives, and a DVD-ROM drive as the only slave.

When I try to boot the CD, I get a white screen.  I can see the ATA card when I do **dev / ls** at an Open Firmware prompt, but I guess I'm not smart enough to figure out how to specify the DVD-ROM drive.  :sad: 

Any pointers, anyone?

P.S.  I installed Ubuntu on another PPC machine.  I was pleasantly surprised to see that the installation was as easy on a Mac as it was on a PC.   Sweet!  =P~

---

### Post by Tommy on 2004-12-04
I'm not sure of the brand, but I believe I have a similar UltraATA card in an "oldworld" PowerMac 9600 and I could NOT install Ubuntu on it because the kernel apparently does not include the driver (also called a Kernel Module) for that card. In order to boot the machine, the driver has to be accessible to the kernel when booting.

I have successfully installed various forms of Debian on that old Mac, though I have had other problems with it.

SO the solution for Ubuntu might be either to find a premade kernel (search Google -- benh kernel), or to compile a custom kernel. Ubuntu has standardized on the 2.6 series kernels, so if you locate or compile a 2.6.x kernel for your Mac that includes that module, you might have more luck.

---

