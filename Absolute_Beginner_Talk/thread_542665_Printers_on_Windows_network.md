---
title: "Printers on Windows network"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2007-09-04
I'm newly running Ubuntu this one computer on a network with two other computers still running MS Windows xp, each of the other two computers have a printer that is shared with the others though them. 

Now on this computer running Ubuntu I can access files and documents on the other computers, but I can not send to the printer. Is this normal? Can I run a printer located on a MS windows machine from here?

---

### Post by mlentink on 2007-09-04
Yes you can.
System > Administration> Printers

select "New Printer" after which the system will start reading the CUPS-database which takes a while on my 1GHz P3...
Then select "Network Printer" and choose "Windows Printer (SMB)" from the list. Enter ( or select form the list) the name of the computer the printer is attached to and the name under which it is shared (or select it from the list).

That's it.

---

### Post by niceguy123 on 2007-09-04
Thanks, That was neat.

---

