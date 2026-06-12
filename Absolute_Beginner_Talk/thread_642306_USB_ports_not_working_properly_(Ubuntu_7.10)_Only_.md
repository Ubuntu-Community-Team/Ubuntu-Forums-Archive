---
title: "USB ports not working properly (Ubuntu 7.10) Only one at a time?!?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by jannen on 2007-12-16
I have a laptop (run Ubuntu 7.10) with a laptop card with two USB 2.0 ports. Its been working fine until couple days ago. It only lets you use the other port and only max one hardware at a time (usb modem, mouse, camera etc.) Looks like there is not enough power for more than one port(?)

What could have happen? How can I sort it out... please, I really need help here!

Thanks guys, appreciate quick help!:confused:

---

### Post by rondamato on 2007-12-16
I also kinda have this issue.  I have an HP pavillion desktop running 7.10 and a USB HPLJ4000 printer.  When the OS was fresh (and 2-3 months beyond) I'd plug it in and Ubuntu would detect it, I'd point the installer to the ppd and all was go!

Now, it recognizes the MOUSE in any of the 6 USB ports.  That's all.  I tried a camera, my mp3 player, a memstick, an external HDD--nothing.

Did a lsusb, got this:

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 004: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 003 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

which means nothing.

The printer is recognized perfectly by my Mac G5 next to me right now, so I've been using Samba to print to the Mac from this box (Ubuntu).  Plus I can then share files--as long as "Windows File Sharing" is enabled on the Mac and I log into the Mac with "smbguest" and "guest" or Gnome will scream that it can't log on.

I so far can only see the Mac on the Linux box--no matter what I try I cannot see the Ubuntu box thru the Mac.

If someone comes up with an idea to try for this USB thing please let me know!!!

DoctorRon

---

### Post by jannen on 2007-12-24
Is there any USB experts out there?

Seems no-one in the Ubuntu community knows about USB... ???:confused:

---

