---
title: "Has anyone had any luck finding a working driver"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by sublimeprogie on 2006-07-14
i have been trying for literally days to get my wireless working in ubuntu.  i am on in ibook g4 and i think the thing i am stuck on is getting a driver for my airport card, has anyone found a driver that they have had success with?  or is there a way to copy the driver from my OS X side of the computer to a cd and do it that way

---

### Post by Jagot on 2006-07-14
can you post the result of this command in terminal:

```
lspci
```

---

### Post by sublimeprogie on 2006-07-14
```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M11 NV [FireGL Mobility T2e] (rev 80)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
```

---

### Post by adam.tropics on 2006-07-14
I don't have a mac, but have you tried [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDevice%2FAirportExtreme") wiki entry, it claims to include the g4 airport stuff.

---

### Post by Jagot on 2006-07-14
You can also just do a search for your card on the forums - same as mine - Broadcom 4318.

---

### Post by sublimeprogie on 2006-07-14
thanks alot guys, i will give it a go, i hope this works it will make learning lot easier

---

