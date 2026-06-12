---
title: "usb/headphone port weirdness"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-12-06
Ok, so I've had this problem since I first installed Ubuntu.. I have a total of 3 usb ports on the front of my machine.. it's an hp pavilion a630n. The usb port next to the ms and sd slot works fine.. however the other 2 usb slots that are next to the headphone jack, as well as the headphone jack don't work properly. The usb ports just wont work.. the headphone jack works, BUT sound still comes out of the speakers so if I want to listen to headphones I just turn the speakers all the way down!! LOL! Anyone have any ideas on how to test the usb ports and how to get the headphone/mic ports to function properly?? Thanks!! :)

---

### Post by Mark_in_Hollywood on 2007-12-06
Open a terminal and do:

sudo lsusb

post the output of that here in this thread.

---

### Post by andyho on 2007-12-10
Sorry it took me a couple to get back to ya! Now.. besides the 3 I have on the front of my machine, there's 4 on the back as well.. the cam and router are using two on the back, the printer is using one on the front. If that might help ya narrow down which ones are which with the output. Thanks!!

andyho@andyho-ubuntu:~$ sudo lsusb
Password:
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 03f0:2d11 Hewlett-Packard OfficeJet 6110
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 001 Device 001: ID 0000:0000

---

### Post by andyho on 2007-12-13
Well I've been able to figure out the USB part of things, but my headphones are still being wonky... I'm sure it'll just take some more tweaking. But at least one thing is figured out! :popcorn:

---

