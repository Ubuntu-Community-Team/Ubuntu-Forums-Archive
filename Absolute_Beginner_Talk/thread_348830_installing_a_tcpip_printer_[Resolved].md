---
title: "installing a tcp/ip printer [Resolved]"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by cbrody on 2007-01-29
I am trying to install a TCP/IP printer.  The printer is a Kyocera and I have already installed the PPD.  Unfortunately, when I try and set it up as a network printer, I am not offered the choice of putting in the tcp/ip address.  In the printer properties, I look at the connection tab and I selected CUPS Printer (IPP).  For the URl:  I typed in ipp://linux-desktop:631/printers/192.168.3.20 and I also tried  ipp://linux-desktop:631/printers/FS5030N which is the printer name.  Where am I supposed to put the IP address of this computer?  My other printers which are connected via USB are showing up and printing.  Thanks for any help you can provide.

CB

---

### Post by taurus on 2007-01-29
Instead of using CUPS, try to pick LPD and enter the IP address of your network printer.  Use lpr as QUEUE and it should work since I can print my stuff to two HP LaserJet 4200 network printers and a Dell 310cm color network printer from my Ubuntu in the office.

---

### Post by cbrody on 2007-01-29
Thank you.  It works.  Case resolved.

I really appreciate the help.

CB

---

