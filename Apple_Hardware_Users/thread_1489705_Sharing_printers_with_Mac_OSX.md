---
title: "Sharing printers with Mac OSX"
date: 2010-05-21
forum: Apple Hardware Users
---

### Post by mbeierl on 2010-05-21
I've got my printers attached to an Ubuntu server which is sharing them using the regular printing service.  I can see the printers from other Ubuntu machines without a problem, but I cannot figure out any method of seeing them or adding them to my Macbook.

Any help on how to troubleshoot this is greatly appreciated.

---

### Post by cariboo on 2010-05-21
Moved to apple users.

---

### Post by linuxopjemac on 2010-05-21
Applications -> Utilities -> Printer Setup Utility
Add
IP Printer
Protocol IPP
address: IP address, e.g. 10.0.0.2
Then set the printer driver. 

I have the same. I use an HP printer connected to a Linux computer using CUPS. I setup the same on my MacBook.

---

### Post by mbeierl on 2010-05-27
Thanks!  I have two printers on the same server host.  How do I tell them apart?

---

### Post by Morbius1 on 2010-05-27
Examples:


ipp://192.168.0.100:631/printers/Linux-Printer-Name1

ipp://192.168.0.100:631/printers/Linux-Printer-Name2

---

### Post by mbeierl on 2010-05-27
When I tried that I get (from memory - not at my mac right now) a "bad port number" error message (as soon as I enter :631) in the url

---

### Post by Morbius1 on 2010-05-27
Sorry about that. I'm used to doing it from the "Advanced" icon ( which you may not have ) not the "IP" icon.

In the IP section:

Protocol: Internet Printing Protocol

Address: 192.168.0.100:631

Queue: printers/Linux-Printer-Name

---

