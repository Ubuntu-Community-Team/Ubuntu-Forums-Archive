---
title: "[SOLVED] Problems Installing Graphic Card"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Settler on 2007-12-14
Hello,

everything works fine on my new Ubuntu 7.10 except the resolution of my monitor. To my thought this is because of the drivers for my "ASUS EN6600/TD PCI-E 128MB TVOUT DVI RETAIL" which i've never installed in. And one thing to ask!

1. I don't know how to update or install the drivers for this card so that I can have the resolution and the refresh rate wanted. Do you know?

---

### Post by RomeReactor on 2007-12-15
Hi. The drivers to be installed depend on what chipset the graphics card has. Please open a terminal (Applications->Accessories->Terminal) and run the following commands:
```
lspci | grep VGA
```
and
```
sudo lshw -C display
```

Post the results of both commands, and then we'll see which drivers are needed.

---

### Post by Settler on 2008-01-09
lspci | grep VGA

05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

and then

lshw -C display

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NV43 [GeForce 6600]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: latency=0


so any solution ?

---

### Post by PmDematagoda on 2008-01-09
You should be able to install the drivers for your VGA card through the Restricted Drivers Manager which is found in System>Administration>Restricted Drivers Manager.

---

### Post by Settler on 2008-01-09
Done thanks a lot!!!

---

### Post by rulixx on 2008-01-26
Sorry for that question: I can't find "System>admini..>Restr.."
But may be it's due to Kubuntu.
I've got a comp. with the Asus EN6600 card, with the nvidia chips, my KnowHow installing drivers is quite limited.

But in any case I'm happy that this card is on the Whitelist for Linux.
(XP already running with this card, but had to search for the driver also. The same was necc. for the Realtek HD ALC662 chip)

But how should I go one?  Restricted drivers is activated already.

---

### Post by rulixx on 2008-01-28
All o.k.
I installed Gutsy and the installation of the restricted driver for the Gforce 6600 was selfexplaining.
Also the HDA Audio was recognized and installed by the install proc.

Ubuntu is definitely easier to be installed compared to  Win.

So sorry for my request:guitar:

---

