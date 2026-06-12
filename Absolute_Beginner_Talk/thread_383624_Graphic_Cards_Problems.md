---
title: "Graphic Cards Problems"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Phntm Black Ice on 2007-03-13
Ok I installed xubuntu as a dual boot with WinXp got it installed and all working.  But it was using my Cirrus Logic old graphics card and wanted to do dual screen or at least use the Geforce4 MX440 graphics card instead since it is better graphics card.  
So i tried the TwinView command and when tried relogging I get black screen.  With the following error.  > Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose problem.
This brings up the following:
Log file: /var/log/Xorg.0.log
Using config file  /ets/X11/xorg.conf
WW   NVIDIA: No Matching device section for instance (BusID PCI:1:0:0) found
EE     No devices detected

Some addtional information:

PCI : (0:9:0) Cirrus Logic GD 5165 [Laguna} rev2
PCI : (1:0:0) nVidia Corporation NV17 [Geforce 4 MX440] rev163

The Cirrus Logic is a pci graphics card, while the Geforce 4 is an AGP card.  I have 2 screens and use 1 card for each screen under Windows.  Would like to at least use the Geforce card for Linux if dual windows is not an option or difficult to implment.


So I then went into safe mode and tried    sudo dpkg-reconfigure xserver-xorg but no luck.


I am a total newb with Linux so if you can help or need more information please be very specific.  What may be common practice for you may leave me lost in no time.

Thanks.

---

### Post by Phntm Black Ice on 2007-03-14
Any one?

---

### Post by alienexplorers on 2007-03-14
run lspci and post results

---

### Post by Phntm Black Ice on 2007-03-15
I type in lspci and it gives me a range of commands that can be used with it, thats all.

---

