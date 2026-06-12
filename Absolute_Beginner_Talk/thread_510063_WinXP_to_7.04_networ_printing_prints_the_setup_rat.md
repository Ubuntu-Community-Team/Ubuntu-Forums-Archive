---
title: "WinXP to 7.04 networ printing prints the setup ratherjob request not the job itself"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Nathan Scott on 2007-07-26
Ubuntu 7.04 (intel based box)
WinXP (Dell D800)
Fuji Xerox C525a printer connected to locally to Ubuntu server via USB

Hi, moving from a Vista server to a ubuntu server (the cost of vista being silly and ubuntu seeming a solid option) everything has gone fine apart from printing from winxp to the ubuntu network printer.

-Printing locally from Ubuntu works fine.
-Can see the CUPS from the remote PC browser :631 port
-Using winxp wizard to add the printer appears to work and have chosen the driver that worked ok when vista was the server

But when I print anything it prints a job description not the actually output eg
@PJL comment TIME = 9:20
@PJL comment DNAME=Test Page
@PJL Job Mode = printer
@PJL Set qty = 1
@PJL Set copies = 1
and other setting type info.

have set the network address to:
[http://192.168.2.1:631/printers/FUJI_XEROX_DocuPrint_C525_A-AP_USB_1](http://192.168.2.1:631/printers/FUJI_XEROX_DocuPrint_C525_A-AP_USB_1)
which is the name which shows in cups administration screen

Any one can help?

---

### Post by linuxwizard on 2007-07-26
Might be something here that will help you

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

