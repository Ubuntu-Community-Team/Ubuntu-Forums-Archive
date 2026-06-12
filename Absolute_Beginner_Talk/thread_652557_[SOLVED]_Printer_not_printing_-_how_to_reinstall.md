---
title: "[SOLVED] Printer not printing - how to reinstall"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-28
Output of lsusb:

mark@Lexington-19:~$ lsusb
Bus 004 Device 004: ID 06e1:d804 ADS Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 13fe:1a00  
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 03eb:3301 Atmel Corp. at43301 4-port Hub

the above from after boot.

If I unplug and re-plug the usb cable:

mark@Lexington-19:~$ lsusb
Bus 004 Device 004: ID 06e1:d804 ADS Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 009: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer**
Bus 001 Device 008: ID 13fe:1a00  
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 03eb:3301 Atmel Corp. at43301 4-port Hub

How do I fix this?

---

### Post by spiderbatdad on 2007-12-28
so does the printer work after you plug it in again? or is it "cold plugging," boot time configuration you're trying to accomplish?

---

### Post by Mark_in_Hollywood on 2007-12-28
> **spiderbatdad said:**
> so does the printer work after you plug it in again? or is it "cold plugging," boot time configuration you're trying to accomplish?

Yes, the printer will print after being "hot-plugged". NO I'm not doing "cold plugging".

More to the point: do I need to uninstall and re-install the "drivers" and can you point me to a "how-to" for a Brother Laser HL-1440, if that's the solution. 

Otherwise, why would the us-bus not see and then see the device?

---

### Post by disturbed1 on 2007-12-28
Common problem with some Brother printers.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/35638](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/35638)

> 
The Brother USB implementation is full of bugs like this. Assuming that any
fix is possible, it will have to come from the kernel folks, because we
depend on the USB printer driver (character device) to get the 1284 device
ID from the printer.

---

### Post by Mark_in_Hollywood on 2007-12-28
> **disturbed1 said:**
> Common problem with some Brother printers.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/35638](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/35638)

I read the bug report. I'm going to disagree with you here. The printer has worked fine since Breezy Badger and only in Gutsy have I seen a problem. For the record, the printer is detected and "sits" as default printer in System/Preferences. Thanks.

How do I uninstall and re-install the drivers? Anyone?

---

### Post by Mark_in_Hollywood on 2007-12-29
Go Figure!
(I've had too many of these)

So after a few reboots, the printer is no longer unseen by the OS. I have changed nothing. I have done a lot of lsusb, but what would that matater.

Go Figure!

---

