---
title: "what drivers do i need?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by davedom on 2008-01-20
I am going to install ubuntu 7.04 and was wondering what drivers I will need. I have the following specs;

ASUS m2n4-sli
amdx2amd4200dualcorecpu
2.2ghz, fsb;1600mhz cache 1mb ram support ddr2

nvidia nforce chipset (4sli)

2gb (4x512mb modules)
realtek ac97 5.2 channel audio codec
samsung 500gb 7200rpm/16m
serial ata 3gb/s
samsung lightscribe 18xdvd+/-rw/r writemaster tm 
xpert vision geforce 8500gt pci express
nvidia geforce chipset
512mb memory ddr2 128bit

linksys wusb 54g ver 4
wireless g usb adaptor
802.11g 54mbps 2.4 ghz

lexmark z615

---

### Post by loudnlownoma on 2008-01-20
Best way to find out would be booting up the LiveCD.  Once it's loaded, see what works.  That will give you an idea of what you will need to look for as far as installing drivers and which hardware isn't picked up and identified automatically.

---

### Post by jleaker01z on 2008-01-20
Most of what you need will be installed automatically.  You will need to install your nvidia drivers after you install, but you dont need anything extra for that.  It is in the Ubuntu software repositories, and there is also a program called 'envy' that will do that for you.

The wireless card you will have to use a program called ndiswrapper to install (probably).
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

The Lexmark printer you will need to follow these directions:
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605)

---

