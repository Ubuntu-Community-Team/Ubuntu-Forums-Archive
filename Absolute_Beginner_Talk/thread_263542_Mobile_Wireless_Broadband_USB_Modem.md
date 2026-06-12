---
title: "Mobile Wireless Broadband USB Modem"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by bryan4134 on 2006-09-23
Huawei's hsdpa modem Model E220

The E220 provides mobile broadband via USB 2.0 and works flawlessly under Windows. While I can "see" the modem in Device Manager...see attachment.... I am too much of Linux newbie to know how to proceed from here. I would be interested to hear if anyone has managed to get this neat little 3.6mbps wonder working with Ubuntu.

Any help advice appreciated.

Thanks, Bryan

---

### Post by b_martinez on 2006-09-23
Read this, it may help out.

[http://the.taoofmac.com/space/Huawei/E220](http://the.taoofmac.com/space/Huawei/E220)

hth
Bill

---

### Post by bryan4134 on 2006-09-23
Sorry to be dumb - that rference tells me to create a script with the following....

modprobe usb-ohci
modprobe usb-uhci

modprobe usbserial vendor=0x12d1 product=0x1001
modprobe usbserial vendor=0x12d1 product=0x1003

mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB1 c 188 1
mknod /dev/ttyUSB2 c 188 2

Can you point me in the right direction to learn how to do this?

Thanks, Bryan

---

