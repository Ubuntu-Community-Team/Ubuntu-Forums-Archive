---
title: "Need help installing scanner on Feisty please"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-04-28
I have an 'Epson Perfection 1260' scanner which I am hoping to hook up to my Feisty computer.

Unfortunately I didn't see any way to do this (I had hoped it would be like hooking up a printer)

I would appreciate it if someone could tell me whether I should be able to do this.

---

### Post by sharke on 2007-04-28
Your scanner is supported.
Boot computer with scanner on  and in a terminal do lsusb is your scanner shown. If If shown we need the bus location which should be something like 005 014 .We then  have to change the permission of that bus .
In terminal do sudo chmod a+w /dev/bus/usb/005/014 (substitute your bus id).
Start xsane and hope it works.
Regards
Sharke

---

### Post by L Campbell on 2007-04-29
> **sharke said:**
> Your scanner is supported.
Boot computer with scanner on  and in a terminal do lsusb is your scanner shown. If If shown we need the bus location which should be something like 005 014 .We then  have to change the permission of that bus .
In terminal do sudo chmod a+w /dev/bus/usb/005/014 (substitute your bus id).
Start xsane and hope it works.
Regards
Sharke

Thanks for your help.

qwer@qwer-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04b8:011d Seiko Epson Corp. Perfection 1260 Photo
Bus 001 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 001: ID 0000:0000  
qwer@qwer-desktop:~$ sudo chmod a+w /dev/bus/usb/001/003
Password:
qwer@qwer-desktop:~$ 

Just one other thing, if you don't mind, how do I get to ' xsane '?

---

### Post by L Campbell on 2007-04-29
> **L Campbell said:**
> Thanks for your help.

qwer@qwer-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04b8:011d Seiko Epson Corp. Perfection 1260 Photo
Bus 001 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 001: ID 0000:0000  
qwer@qwer-desktop:~$ sudo chmod a+w /dev/bus/usb/001/003
Password:
qwer@qwer-desktop:~$ 

Just one other thing, if you don't mind, how do I get to ' xsane '?

Here I am, talking to myself.   :-)

I have it figured out now and am ready to start scanning.

Kind regards.

---

