---
title: "Problems installing on PowerMac G4 MDD"
date: 2010-01-24
forum: Apple Hardware Users
---

### Post by cheezy13 on 2010-01-24
It's been a while since I last installed Ubuntu on my G4 MDD. First install, about 4 or 5 years ago, was fine. I was even able to install and run XGL/Compiz effects, and all that stuff. Then I had to reformat the drive because I need it for a Mac OSX install, which was more vital than Ubuntu. Now, it's been several months I've been trying to re-install Ubuntu and every distribution I've tried so far desperately failed. Let me explain : I can boot from the live CD, get the boot prompt, start the boot, but then after a while, the screen goes black, my LCD screen says "no input signal", and finally, my Mac won't boot back to Mac OS X until I reset the motherboard and remove the cd from the drive…

I tried almost every Ubuntu PPC distribution, to no avail.

What changed in my computer since I last managed to install Ubuntu PPC (was a 6.x by then I think…) is I installed a Pinnacle PCI video digitizing card and an Adaptec ultra-scsi card (PCI as well). Can some type of hardware incompatibility prevent Ubuntu from booting properly?

Thanks.

---

### Post by linuxopjemac on 2010-01-24
I would do a server installation without a desktop. Then you add the GUI later, if you are confident with that. So you won't run into the X problem with the installer.

[http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-server-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-server-powerpc.iso)

---

### Post by tiresia on 2010-01-24
Or you can remove any extra PCI cards, install linux and put them back after the installation. I had often similar problems even with usb cards

---

