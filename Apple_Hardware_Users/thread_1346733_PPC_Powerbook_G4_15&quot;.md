---
title: "PPC Powerbook G4 15&quot;"
date: 2009-12-05
forum: Apple Hardware Users
---

### Post by SethDG on 2009-12-05
So I've successfully installed karmic koala on my powerbook g4, 15". The wireless is up and running. I had a minor issue with screen flicker but after a few restarts its not happened since the initial wireless connect. 

Now there are a few quirks I"m trying to work out. The fan is running full speed non stop, and the touchpad is like a skeleton of its former self. No double tapping, no dragging, i just feel naked.

Here is my system:

goforever@GO-laptop:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:13.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:24:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

I'm rather new to linux. How can I do these little hardware tweaks?
And does anyone know a good (organized) database for troubleshooting this stuff?

---

### Post by rednose0607 on 2009-12-05
Hello,
for the fan, just disable the module therm* in /etc/modules. Is a suggestion I found here in the forum. No prob so far. If you want to know more just search for "karmic ppc fan"

For the pad, I can only say that it works fine on my pb, UNTIL I close the lid. After the suspend resume cycle it freeze. The mouse works fine though. Just recall to rmmod b43 before suspendig or shutting down the pb, or it will prevent a happy power mgmt.

Bye

---

