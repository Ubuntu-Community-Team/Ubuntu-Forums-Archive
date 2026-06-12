---
title: "Trust 380 USB 2.0 Spacec@m - How can I make this USB Webcam work?"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-12-04
Hello!

I would like to setup a **Trust 380 USB 2.0 Spacec@m** with my Ubuntu v6.10.

But I do NOT know how to do it...

Where do I start from?

Thanks.

---

### Post by dvarsam on 2007-01-03
Hello again!

Using the Terminal window & typing "**lsusb**" & get the following output:

> root@dimitris-desktop:/# **lsusb**
Bus 005 Device 005: ID 0e96:c001 Aplux Communications, Ltd 
Bus 005 Device 004: ID 0a48:3240 I/O Interconnect 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0df7:0620 Mobile Action Technology, Inc. MA-620 Infrared Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

I am sure that it is the above first line!
E.g.: **Bus 005 Device 005: ID 0e96:c001 Aplux Communications, Ltd**

I also installed the package "camorama" & when from the Menu I select "**Applications\Graphics\Camorama Webcam Viewer**", I get the following window:

> _Title_: Error: Camorama
_Message_: Could not connect to video device (/dev/video0).
Please check connection.
_Button Available_: Close (only!)

Any ideas on what to do next?
Thanks.

P.S.> Should I try to install package "spca5xx" or "quickcam"?

---

### Post by OffHand on 2007-01-03
Best advice I can give you to check what drivers it uses (and install those) and to check if your cam is supported.

---

### Post by dvarsam on 2007-01-03
> **OffHand said:**
> Best advice I can give you to check what drivers it uses (and install those) and to check if your cam is supported.

How can I check what drivers it uses?
And how can I check whether my cam is supported?
You mean from here:

[http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml](http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml)

Or somewhere else?

Thanks.

P.S.> My Webcam model is **Trust 380 USB 2.0 Spacec@m**. And in that site, under sections 4.2 & 4.4 I get the following info:
_Section 4.2_: for "**Trust SpaceC@m Lite USB** & **SpaceC@m 100**" - does not seem to be mine
_Section 4.4_: for "**Trust Sp@ceC@m USB**" - this is too vague too!
What do I do?

---

