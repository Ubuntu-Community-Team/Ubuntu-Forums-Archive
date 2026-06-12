---
title: "trying to install hp scanjet 4670 with Feisty Fawn"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-05-12
Hi, I'm trying to install hp scanjet 4670 with Feisty Fawn.  I looked through some previous threads.  When I click on "xsane image scanner" I get "no devices available.

I went to terminal and tried to follow some previous directions.  This is what I've gotten so far:
ammmom@ammmom-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. 
Bus 002 Device 003: ID 04f9:0028 Brother Industries, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 03f0:3005 Hewlett-Packard 
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. 
Bus 001 Device 001: ID 0000:0000  
ammmom@ammmom-desktop:~$ sudo chmod a+w /dev/bus/usb/001/005
Password:
ammmom@ammmom-desktop:~$

---

