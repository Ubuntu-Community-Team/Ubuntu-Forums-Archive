---
title: "dvb-usb help"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by BFPerkins on 2007-11-14
Hi all.
I have a Terratec Cinergy Diversity usb tuner. I have found a number of forum posts saying it's possible to use it, but these all assume that the usb adaptor is recognised as a dvb-usb device.

after loading the dvb-usb-dib0700 module, all I am getting from dmesg when I plug my device in is:

"
usb 1.6: new low speed USB device using ehci_hcd and address 6
usb 1-6: configuration #1 chosen from 1 choice
"
According to the debug log, it is being picked up by the network manager.

The tuner is not seen by the dvb-usb-dib0700 module, and the onboard IR receiver is not recognised by Lirc either.

I am running 7.10 64bit on an asus m2n32-sli deluxe with an amd athlon x2 2G

Any ideas? Or am I being completely dense?

---

### Post by ddrichardson on 2007-11-15
I don't know if this is working with 64 bit versions yet.

---

