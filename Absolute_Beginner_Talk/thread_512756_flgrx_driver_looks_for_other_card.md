---
title: "flgrx driver looks for other card"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by random_user on 2007-07-29
Hi, I use dual head with my pci ati radeon 9250 (one monitor on VGA out, the other on DVI out).  Unfortunately, most games I try to play run extremely slow, I'm assuming this is because I don't have the proper driver for my ati card (I use radeon at the moment).  My guess is that I need fglrx, however after installing that driver and then changing my xorg.conf so that it uses fglrx driver (I don't change anything else, I have tried with and without the "composite" "0" thing), however when I boot up after changing to fglrx, logs show that no matching device for PCI 1:1:1 could be found, and so it doesn't work.

My guess is that PCI 1:1:1 is the DVI port, because lspci lists PCI 1:1:0 as my VGA output.  Am I completely missing something that would cause this not to work properly?

Something to note:
In my xorg, both of my Device sections are listed with pci 1:1:0 since it was the only thing that seemed to work, it didn't like when I explicitly stated two different pci values for VGA and DVI ports.  Hopefully this isn't all confusing, any help or advice would be much appreciated! Thanks!

---

### Post by ronocdh on 2007-07-30
The link in my sig should be provide the correct method for getting you up and running with fglrx.

---

### Post by pistcivet on 2007-07-30
fglrx driver is for ATI 9500 or higher. sorry.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

