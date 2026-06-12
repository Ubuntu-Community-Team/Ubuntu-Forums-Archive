---
title: "Virtualbox, win xp and webcam logitech c910 problem"
date: 2011-10-26
forum: Any Other OS
---

### Post by balsamico on 2011-10-26
hallo
i have linux mint 11 and virtualbox 4.1.4
inside the host is windows xp sp3
i have webcam logitech c910 EHCI
and under linux work perfectly
i have enabled usb, ehci all ok
when i start the software to install it inside the windows xp it ask at beginning to conenct webcam
i do, windows found it, say me there is a logitech c910 connected bla bla...
it isntall all the software but at the end...it no work
windows say there is a problem with driver
i had reinstall it lot times cold no cold start
i had even reinstalled ALL windows with sp3 and than only the software for webcam
so i'm sure no conflicts with other softwares or a bad installation...
into a machine totaly winxp sp3 the driver work properly

this is the log of virtualbox after i conenct webcam:
02:37:26.127 VUSB: attached '00007fd654c17180[proxy 046d:0821]' to port 1
02:37:26.132 EHCI: USB Operational

and my lsusb is:
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 046d:0821 Logitech, Inc.   <-----this is the webcam
Bus 002 Device 004: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 002 Device 003: ID 046d:0a18 Logitech, Inc.
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6364 Alcor Micro Corp.
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

if i open the Hardware source of win xp i read: impossible to open driver code error 10


can someone help me?

---

### Post by zettabyte on 2012-04-06
I was getting the same ``Code 10`` error in Windows 7.

In Windows 7 64bit, I went to the Device Manager, found the USB device, and rolled the Driver back from the Driver tab in the Properties window.

Here are the driver details it now displays:

Driver Provider: Logitech
Driver Date: 1/17/2012
Driver Version: 13.31.1044.0
Digital Signer: Microsoft Windows Hardware Compatibility Publisher

Not sure if it will help in XP, but it got may camera working in 7.

---

