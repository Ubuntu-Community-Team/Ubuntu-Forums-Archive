---
title: "Network Printing Problems"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by kurniawands on 2006-07-17
:-? any body wants to help me ???

i used to be a windows user till couple days ago... hehehe so i'm definitely newbie here... dapper is my first distro... :D 

everything was doing well, system, applications, dvds, music everything was just fine... except one thing, printers.

i got hp deskjet 845c and laserjet 1020 on the network and i don't know how to set those printers. first printer (845c) was found on the network but can't print anything. second printer ? worse, seems not recognized (didn't found on network)...

what to do guys... ??? do i need... drivers ? or script (as i did for dvd thing since libdvdcss is no longer available on ubuntu's source) ?

Help me..... ](*,)

---

### Post by simone.brunozzi on 2006-07-17
do you use ubuntu or kubuntu?
They have some different tools to handle printing.

However, I suggest you to use CUPS and configure it.
Cups is on localhost on port 631:

[http://127.0.0.1:631/](http://127.0.0.1:631/)

Cheers,

---

### Post by kurniawands on 2006-07-17
i'm using ubuntu

i have tried that cups, but i still can't see my 1020 laserjet and still can't print using 845c. btw, i'm still using windows network... :( any other advice ???

---

### Post by drtvasudevan on 2006-07-17
i can see both listed in the printer data base.
the way to install the drivers:click system>admin>printing.
follow the wizard.
if the printer was powered up and function during boot it should be recognised.i see both the printers in the data base and so should install the drivers.
in case it asks for the ppd file go to linuxprinting.org and get it.

---

### Post by monkieie on 2006-07-17
now here's a really stupid question - but it needs to be asked;

have you activated both of the printers in the Windows network for network sharing? :-#

Or are you just accessing the printers directly on the network?

---

### Post by drtvasudevan on 2006-07-17
here are the ppd
go to these pages and click on download ppd:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C)

---

