---
title: "What are CUPS Services, how to turn off"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-05-06
I read this in one review of Feisty Fawn :

Ubuntu now seems to be more usable than before with 256 MBs of RAM (with CUPS services turned off) 

What are CUPS Services, and  how does one turn it off ?

---

### Post by jiminycricket on 2007-05-06
[CUPS ]("http://en.wikipedia.org/wiki/Common_Unix_Printing_System")

Turn off temporarily with: sudo /etc/init.d/cupsys stop 

A package in universe called " bum" also lets you turn off startup services.

---

### Post by darkrose on 2007-05-06
CUPS = Common Unix Printing System
It's what enables you to print.

to turn off I think you go to:
system --> administration --> services and dissable CUPS (not on a gnome desktop at the moment so can't be sure.
otherwise you can disable it permanently from the command line with:
sudo rm /etc/rc5.d/S19cupsys

---

### Post by Skrynesaver on 2007-05-06
Common Unix Printing System
It allows a linux box to act as a print server for itself or any other machine on the network.
It provides a web page based printer management interface (quite groovy), try  [http://127.0.0.1:631](http://127.0.0.1:631)
You can tun off/on any service in System>Administration>Services
Printer Services is cupsd

---

### Post by dptxp on 2007-05-06
Thanks.

This is what the WIKI says as per the link given by one of you.

[COLOR="Indigo"]The Common Unix Printing System (CUPS) is a modular printing system for Unix-like computer operating systems that allows a computer to act as a powerful print server. A computer running CUPS is a host which can accept print jobs from client computers, process them, and send them to the appropriate printer.[/COLOR]

Will disabling affect LOCAL printing too ? If yes, then I shall turn it off by one of the two methods given by you.

The IP address given is obviously invalid- 5 bytes, a colon and a value exceeding 255.

---

### Post by darkrose on 2007-05-06
CUPS is required for local printing as well.

:631 is the port number that CUPS listens on, the address sends you to Internat Protocal address 127.0.0.1 at port 631.

---

### Post by Skrynesaver on 2007-05-06
127.0.0.1 is known as the loopback address, it always points at the localhost.  Apending a port number onto and address with a colon separation points to that port, take a look in /etc/services to see how many ports/protocols are available.
The above address sends you to the web interface to cups on your own machine.

Yes CUPS is used for printing locally

---

### Post by hartz on 2007-05-06
> **dptxp said:**
> 

The IP address given is obviously invalid- 5 bytes, a colon and a value exceeding 255.

The address is quite valid; 127.0.0.1 is the loopback address (connect to yourself), and the port number determines the service that you want to connect to.

In fact, the default http:// port number is port 80 - This is what you connect to for most normal web pages.

---

### Post by dptxp on 2007-05-07
Actually I clicked on it from my desktop that uses XP.

So I got -" Problem loading page" and "Unable to connect".

There is so much to learn.

Thanks everyone

---

