---
title: "[SOLVED] How Can i Access this USB Drive?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-10-09
Hello, I have some old IDE drives that [I] need to transfer data from. I bought an IDE to USB adaptor, and it also has a power plug. So, it all sits outside my computer. I plug in the power, make sure the drive is set to master mode, and plug in the USB. I already tried in Windows (just because it's supported) and got the message that I have inserted a high-speed USB 2.0 device, and it will operate more slowly than it would if I plugged it into a high-speed port. Still, the drive didn't show up. I plugged it in while running ubuntu, and it didn't show up, but , here's what I get with lsusb:

```
~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 003: ID 04a9:10a0 Canon, Inc. 
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```

The only other usb items plugged in are my canon printer and my logitech mouse, so it looks like the alcor thing must be my ide to usb adaptor (though the box and product have no brand names on them.)

So what can i do to mount / access this thing?

Any help is greatly appreciated.

---

### Post by taurus on 2007-10-09
Reboot Ubuntu while the drive is still connected and on.  Then, open a terminal and post the output of this command after you've logged back in.

```
sudo fdisk -l
```

---

### Post by coldstatue on 2007-10-09
Actually, I hooked it up with an internal power connection, and it worked. 
Thank you.

---

