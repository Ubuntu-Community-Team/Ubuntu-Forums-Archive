---
title: "Webcam Fiasco!!!"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by virtualani on 2007-04-26
How can i install my webcam??

Its a Creative Live Cam Vista IM

Im running Feisty Fawn 7.04

Cheers

---

### Post by Kobalt on 2007-04-26
Try to run the command line *lspci* in a Terminal and copy/paste the output here, so that we can know over which chipset is based your card upon.

---

### Post by virtualani on 2007-04-26
i HOPE THIS MAKES SENSE!

00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

THANKS

---

### Post by Kobalt on 2007-04-26
Can you please do the same with *lsusb*

---

### Post by virtualani on 2007-04-26
Bus 004 Device 002: ID 07ab:fc03 Freecom Technologies USB2-IDE IDE bridge
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 04d9:0420 Holtek Semiconductor, Inc. 
Bus 003 Device 005: ID 03f0:7504 Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 041e:4052 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000

---

### Post by Kobalt on 2007-04-26
I think you can try to get it working using EasyCam 2 : [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

