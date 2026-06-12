---
title: "can't mount cd and dvd on mac mini"
date: 2010-10-23
forum: Apple Hardware Users
---

### Post by Hakimjo on 2010-10-23
cd and dvd I introduce into my ppc mac mini running 10.10 at best recognises cd in the internal drive as "empty media".  The same discs are mounted normally when inserted in an external usb drive.

I would like the internal drive to act normally, what can I do ?  The "additional drivers" utility is not proposing anything.

This is the lspci lsusb listing

aude@Aude:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Unassigned class [ff00]: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Unassigned class [ff00]: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
aude@Aude:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:1400 Holtek Semiconductor, Inc. PS/2 keyboard + mouse controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 05ac:8204 Apple, Inc. Bluetooth HCI [Bluetooth 2.0 + EDR, built-in]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 152e:1640 LG (HLDS) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
aude@Aude:~$ 

btw  the pci mouse is not working either

---

