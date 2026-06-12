---
title: "Ubuntu on Bootable USB Drive / Key"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by ThetaAldebaran on 2006-08-22
Hi, Ubuntu and Linux neophyte here.

Interested in playing with the OS and want to install Ubuntu on a USB Drive / Key.

I have read that it is best to have 2GB of space for the OS plus more for data, so I believe it would be best to put it on a USB hard drive.

I am looking for advice on how to partition the device and install it.

My motherboards support bootable USB.

Thanks,

Theta

---

### Post by kpurcell on 2006-08-22
If you run the LiveCD it will have an Install icon on the desktop.  Just run it and when it asks for the disk to isntall to, point it to the external hard drive.  Works like a charm and you don't even have to change the boot sector of the internal drive.  Just, when you are booting, tell your computer to boot to the USB drive first.  Then the hard drive.  When it is installed it will boot.  Partitioning is not hard.  You can just let it do it itself otherwise I would give yoru swap about twich your installed RAM.  Give your boot sector at least 5-10 GB and then your home sector the rest.  There is no need to have more than 3 partitions.

---

### Post by XopherY on 2006-08-26
I may want to do something similar too.  I have a 180 GB external USB hard drive that I use for backing up my 120 GB internal hard drive, so it seems like I should be able to partition it to have plenty of room for both back-up and an ubuntu install.

But here's what I wonder about.  If I change to boot sequence in BIOS to boot USB before internal hard drive, won't it *always* boot ubuntu unless I physically disconnect that drive during boot-up?  That seems like a pain.

Is there some sort of boot-loader thing that I can install to allow me to choose which OS I want at start-up?

---

### Post by bodhi.zazen on 2006-08-26
When you install Ubuntu it will install GRUB. GRUB will allow you to select you which OS to boot

Just install GRUB to the USB drive and NOT the MBR.

---

