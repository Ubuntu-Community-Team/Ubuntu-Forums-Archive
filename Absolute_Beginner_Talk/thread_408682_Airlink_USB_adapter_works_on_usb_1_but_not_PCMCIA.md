---
title: "Airlink USB adapter works on usb 1 but not PCMCIA"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by PAPutzback on 2007-04-13
I ahve a Compaq Armada 1750 and when I plug my airlink Ethernet adapter into the 1 usb 1.0 port on the laptop I can get on the net fine. But if I try to plug it into my Zonet USB/Firewire PCMCIA card I don't get a thing. But the Zonet card works fine with a USB flash drive.

I am running XUBUNTU 6.10. 

Thanks.

---

### Post by Austin_KW on 2007-04-13
Open a terminal
After you plug it in what is the output of "dmesg | tail -20" and "lsusb" and "lsmod"

---

