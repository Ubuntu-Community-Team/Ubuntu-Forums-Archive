---
title: "USB Serial / Com Port"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by dudds on 2006-11-27
Hi guys I was hoping I might get a pointer in the right direction. On my Windows notebook I had a USB serial / com port, but of course the drivers supplied are only for windows. Is anyone aware if this is possible to get working under Linux?

If someone with experience in this matter could point me in the right direction I'd appreciate it heaps. I needed to use this port under Minicim.

Cheers,
David

---

### Post by IYY on 2006-11-27
I have never used such a device in Linux, but I think I know what you are talking about. Maybe this can help:

[http://www.linux-usb.org/USB-guide/x356.html](http://www.linux-usb.org/USB-guide/x356.html)

---

### Post by dudds on 2006-11-27
Thank you I'll have a look at it to see if it helps.

David

---

### Post by dudds on 2006-11-27
I've come across other data if this helps:

Ive run the command 
david@homer:/dev$ lsmod | grep usb
usbserial              31336  1 pl2303
usbhid                 39904  0
usbcore               130820  6 pl2303,usbserial,usbhid,ehci_hcd,uhci_hcd


and also the command
david@homer:/dev$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0557:2008 ATEN International Co., Ltd UC-232A Serial Port [pl2303]
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 047d:101f Kensington PocketMouse Pro
Bus 001 Device 001: ID 0000:0000


Perhaps I'm not telling Minicom the right port to use, but I've configured it to use /dev/tty0 /dev/tty1 and /dev/ttyUSB0 however none of these seem to work.

---

### Post by dudds on 2006-11-27
Ok this is weird. In the post above I said I tried setting Minicom to use /dev/ttyUSB0 as the serial port which didn't work. I then just did it again and hey presto it now works. Maybe I made a typo or something. Who knows!!

---

