---
title: "Any reason my USB rf wireless mouse isn't working"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by TheNorthWaves on 2007-12-08
I have a logitech rf wireless usb mini mouse - works immediately when plugged into my mac (os 10.5.1) and windows vista equipped thinkpad. When I run ubuntu 7.10 off the disc in my thinkpad, it won't detect the mouse. Any ideas?

---

### Post by philinux on 2007-12-08
With it plugged in whats the output of

[FONT="Courier New"]**lsusb**[/FONT]

---

### Post by TheNorthWaves on 2007-12-08
I don't know what 1susb is. I looked in the hardware information/manager section.
What I did find is that a Logitech HID device is plugged into USB UHCI controller 5. So it seems to be recognizing that something made by logitech is plugged into a USB port, but it doesn't seem to have any other info available than that. I am a complete nOOb so please bear with me. I'll try my best to learn, but it's slow.

---

### Post by philinux on 2007-12-08
Open a terminal - Apps>Access>terminal anf type in 

LSUSB but use lower case.

Copy and paste the output in a post.

---

### Post by TheNorthWaves on 2007-12-08
First set is without the usb mouse dongle plugged in, the second set is with it plugged in (logitech item)


ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 009: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 009: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 17ef:1003  
Bus 004 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$

---

### Post by philinux on 2007-12-08
ok so the system is picking it up.

Do the same terminal thing with 

dmesg

Post the result of that.

---

### Post by TheNorthWaves on 2007-12-08
will post again...

---

