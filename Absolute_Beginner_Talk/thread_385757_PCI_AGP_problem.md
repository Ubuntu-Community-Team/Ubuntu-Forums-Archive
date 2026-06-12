---
title: "PCI AGP problem"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by jjbean on 2007-03-16
Sorry if this is answered already. I couldn't find an answer by searching. My problem is after installing the driver for my video card the xserver cannot start. Gives me a no device in pci 1.0.0 error. The card is in an agp slot. All was fine until I installed the driver. The card is a Geforce FX 5200. I have tried both drivers from the add/remove and used Fury to install the driver, all with the same result. Everything works fine if i don't install the driver. The card shows up in the device list IDed correctly, but lists it as being in a pci slot as well. The lspci command shows it in pci 1.0.0. So is the pci  versus agp thing my problem? This tech challenged linux newb thanks you in advance for any help. :D Also if it helps the computer is an older Dell Optiplex GX150.

---

### Post by petersjm on 2007-03-16
Might be worth downloading Envy and running that to install the latest Nvidia driver. If you still don't have X, then run "sudo dpkg-reconfigure xserver-xorg" and follow the onscreen prompts. Hopefully, when you reboot, you'll have X again.

---

### Post by jjbean on 2007-03-16
It was the end of a long day I meant Envy, don't know why I typed fury. Sorry about that. I will try the xserver regonfig. When I get to the part for the card location how do I change it from pci to agp?

---

### Post by jjbean on 2007-03-16
Problem fixed, everything is well. When installing Ubuntu to  check it out(lovin it btw), and you use an old computer, it is wise to make sure all cards are properly seated. :oops:

---

