---
title: "Mobile phone suite"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Bauldrick on 2007-09-07
What program can I use to connect and transfer files to/from a samsung e900?

I wouldn't mind just being able to see it as a usb device on the desktop...

dmesg shows this when plugged in:

[  109.476273] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[  109.499257] usbcore: registered new interface driver libusual
[  109.514972] Initializing USB Mass Storage driver...
[  109.515138] scsi0 : SCSI emulation for USB Mass Storage devices
[  109.515228] usbcore: registered new interface driver usb-storage
[  109.515233] USB Mass Storage support registered.
[  109.515451] usb-storage: device found at 2
[  109.515454] usb-storage: waiting for device to settle before scanning
[  114.515584] usb-storage: device scan complete
[  114.522574] scsi 0:0:0:0: Direct-Access     Agere    MMCSD Card       1.00 PQ: 0 ANSI: 0
[  114.701737] sd 0:0:0:0: Attached scsi removable disk sda
[  114.855694] sd 0:0:0:0: Attached scsi generic sg0 type 0

lsusb:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04e8:663f Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Can I put it in fstab or whatever - the device is showing up under Computer as a memory stick icon called "Agere MMCSD Card", but I can't mount it

---

### Post by LowSky on 2007-09-07
have you tried bitpim?

it in the repositories

it might work for you

---

### Post by philinux on 2007-09-07
I just use Gthumb and it mounts and shows my phone and card on the desktop.

---

### Post by LowSky on 2007-09-07
ah.... i forgot about gthumb... that might work too

---

### Post by Bauldrick on 2007-09-07
bitpim doesn't recognise my phone and although I can see the phone as this "memory stick" in >Places>Computer , it is not seen by Gthumb?

---

### Post by philinux on 2007-09-07
Ok this has been puzzling me. If Gthumb mounts my phone and its card why cant the system.
They stay mounted after closing gthumb. And i've got its uuid.

---

### Post by philinux on 2007-09-07
> **Bauldrick said:**
> bitpim doesn't recognise my phone and although I can see the phone as this "memory stick" in >Places>Computer , it is not seen by Gthumb?

you have to click on file import photos. But if its there under places cant you explore it.

---

