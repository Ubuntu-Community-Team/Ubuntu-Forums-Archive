---
title: "USB flash drives won't work"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by miqie on 2008-01-09
I have two USB flash drives that work fine in Windows but are not seen in Gutsy.  I am using a dual boot WindowsXP/Ubuntu computer, so I know that the USB ports work.  Why doesn't Ubuntu see the drives and whats the fix?  They are a Kingston Data Traveler 1GB and an Eagletec 128mb.

---

### Post by annda on 2008-01-09
can you please plug in the devices and then go to the terminal applications>accessories>terminal

and copy & paste the output of this command so that we can see if the devices are even recognized by the system
```
lsusb
```

also, are you plugging them in through a hub?

---

### Post by taseedorf on 2008-01-09
First off, make sure you "safely remove hardware" in Windows.  If you don't, Ubuntu won't auto mount them. It is a bug in Ubuntu, I suppose.   If you go into windows, plug in USB device, than click safely remove, than pull out, THAN put it back in when you start Ubuntu it should work.  If not, you can try a program called hotplug if you don't have it yet.  Otherwise, if nothing works, post the results of dmesg and I can take a look and maybe give you a better answer.

---

### Post by miqie on 2008-01-09
First of all, I am not running them through a hub.  Just directly through the ports on the front of the computer.  I did safely eject them in Windows, but that made no difference.  Here is the output from the terminal window:
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

I have a USB mouse plugged in, which is working and an old Visioneer Onetouch scanner which is not detected by Xsane.

---

### Post by miqie on 2008-01-10
Hi, I am still having problems getting my USB flash drive to work in Gutsy.  I tried leaving the stick in the USB port when I rebooted  and it slowed the boot process down to a crawl.  One thing that did come up right before the login screen was a checklist of what was loading.  I noticed 3 lines: 

USB 5-5  device not accepting address 5 error-110
USB 5-5  device not accepting address 6 error-110
USB 5-5  device not accepting address 7 error-110

then it went to the login screen.  Also, yesterday I loaded "USB View" thinking maybe it could help.  When I put the stick in and open this application I get the message: "Cannot open the file  /proc/bus/usb/devices" and then it says: "Verify that you have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs filesystem mounted."  Does this provide any clues to my problem?

---

### Post by miqie on 2008-01-15
I am still trying to get my flash drives to work.  Can someone offer advice as to how I do the following?  "Verify that you have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs filesystem mounted."  This was a message from the USBView program that I loaded.

---

