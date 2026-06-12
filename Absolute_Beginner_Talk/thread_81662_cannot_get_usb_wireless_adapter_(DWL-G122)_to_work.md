---
title: "cannot get usb wireless adapter (DWL-G122) to work"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by kosiew on 2005-10-24
I just intalled ubuntu 5.10 and am trying to connect to a home wireless network with a D-Link USB adapter DWL-G122.

Currently,
iwconfig

lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

lsusb
Bus 001 Device 004: ID2001:3c00 D-Link Corp. [hex]

I have used ndiswrapper to install the XP driver.

After installing:

ndiswrapper -l
netrtusb driver present, hardware present

But the adapter does not light up as when I use it on Windows XP. The adapter works fine when I dual boot to Windows XP.

also tried 
sudo modprobe ndiswrapper
... I just get a blinking cursor.......

Would appreciate some pointers :
1. how to troubleshoot this further
2. if lsusb can detect the device, why does it not detect the  network

l am a newbie to linux

Thanks in advance.

---

### Post by camj on 2005-10-24
Card: D-Link DWL-G122 rev. A2 (USB)
[LIST]
[*]Chipset: Prism (? correct me please with a more precise chipset name)
[*] usbid: 2001:3704
[*]Label: P/N: BWLG122NA.A2, FCC ID:RRK2004030017-1
[*] Native linux driver: "prism54usb" for 2.6 kernels (as of 2005-Jul-14). I have not tried it.
[*] Driver: 08/05/2004, 3.00.22.0 on the CD (Drivers/PRISMA02.INF; I used it with Drivers/WinXP/PRISMA02.sys, inside, you can find the following: 1-Jul-2004 2.5.12.0), works with ndiswrapper-1.1, kernel 2.4.26 from ALTLinux (std-up-2.4.26-alt12).
[*]Other: "lsusb -v" seems to be able to hang the system at the moment when it scans the D-Link device (probably, this is not related to ndiswrapper).
[/LIST]

Thats coming from the NDISWrapper website at [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

A native driver is available at [http://jbnote.free.fr/prism54usb/](http://jbnote.free.fr/prism54usb/)

---

