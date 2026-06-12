---
title: "printing from a XP box through a ubuntu box"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Dave B on 2007-06-20
i am trying to set it up so that i can print from an XP box through a ubuntu box to a HP 1320 printer.

I am trying to set CUPS up to do this but i am having problems with figuring out IP addresses and setting permissions.

Can someone please walk me through this 

Dave.

---

### Post by schwascore on 2007-06-20
On the Ubuntu box, go to:
System --> Administration --> Printing

Click on Global Settings --> Share Printers

Accept whatever warnings pop up.

On the XP box, do the following:

Settings --> Control Panel --> Printers

Add New Printer --> Network Printer

The device URI should be in this format:
[http://UbuntuComputerIPaddress:631/printers/your_printer_name_here](http://UbuntuComputerIPaddress:631/printers/your_printer_name_here)

Good luck!

---

