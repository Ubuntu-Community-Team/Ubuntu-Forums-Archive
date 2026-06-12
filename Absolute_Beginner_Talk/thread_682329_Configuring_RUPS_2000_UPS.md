---
title: "Configuring RUPS 2000 UPS"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by petnell on 2008-01-29
I'm trying to configuring Megatec RUPS 2000 which has a serial rs232 interface. I brought a serial to USB cable because my PC doesn't have rs232 interface. I'm tried to get Ubuntu to communicate with UPS via USB interface PC interface.

lsusb -v shows
Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2303 PL2303 Serial Port

Niow when i edit Rups config files with communication port as 
/dev/bus/usb/003/005 it doesn't find UPS... 

RUPS Lite - UPS Monitoring Utility. Version 3.11
Copyright(C) Mega System Technologies, Inc. 2003.
Start RUPS...
Press ENTER to continue...
RUPS: Cannot open device (/dev/bus/usb/003/005).

What would be the path name for this??

Regards Aaron

---

### Post by K.Mandla on 2008-01-30
Moved to Absolute Beginner Talk.

---

### Post by petnell on 2008-01-30
Can anyone help me, it supposedly a easy question?

---

