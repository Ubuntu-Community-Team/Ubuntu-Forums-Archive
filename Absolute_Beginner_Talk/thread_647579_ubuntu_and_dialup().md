---
title: "ubuntu and dialup(?)"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by exprof on 2007-12-22
Hi All: 

I'd like to try Lunux, but I am limited to a dialup connection. I've already found that Linux is perhaps not the easiest to use with a modem after some frustrations with Knoppix. I'd like to try Ubuntu, but before I end up reaching for the Ibuprofen again,  I hope that someone out there can tell me if it will be worth the effort.

Here's my setup:

Intel Celeron 1GHz Processor
256 MB RAM
80GB Harddrive
52x CD-RW Drive
USRobotics 56k V.92 PCI Faxmodem

Will Ubuntu work for me?

Thanks in advance...

---

### Post by dstew on 2007-12-22
Maybe. Check [this site]("http://linmodems.technion.ac.il/") for complete information. The best way to figure out if you will be able to get your modem to work is to boot a LiveCD Ubuntu system, then install and use the **scanmodem** utility. The output will tell you exactly what your modem is. It is not possible to tell what kind of chipset your modem uses unless you get more information. You can also issue the command **lspci** in an Ubuntu LiveCD terminal to get more info on your modem.

---

### Post by madjr on 2007-12-22
> **exprof said:**
> Hi All: 

I'd like to try Lunux, but I am limited to a dialup connection. I've already found that Linux is perhaps not the easiest to use with a modem after some frustrations with Knoppix. I'd like to try Ubuntu, but before I end up reaching for the Ibuprofen again,  I hope that someone out there can tell me if it will be worth the effort.

Here's my setup:

Intel Celeron 1GHz Processor
256 MB RAM
80GB Harddrive
52x CD-RW Drive
USRobotics 56k V.92 PCI Faxmodem

Will Ubuntu work for me?

Thanks in advance...

your modem might work out of the box, get the Ubuntu gutsy live CD and it should detect and install your modem.

If it doesn't then get an external "serial" modem (i bought one myself, much better than a regular pci modem)

Actiontec USB/Serial 56K External Modem
[http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1198353430&sr=8-1](http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1198353430&sr=8-1)

great modem, get them while in stock.

then download this fixed version of gnome-ppp
[http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb](http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb)

the fixes are discussed here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487)

---

### Post by Rex72 on 2007-12-22
Im currently using Ubuntu 7.10 on dial up.

Kill all your headaches and purchase the Actiontec external modem off Ebay.

Ubuntu comes with a program that you set up for your dialup connection called nm-applet 0.6.5.  The icon is right next to the clock.

Dial up works great!

---

### Post by exprof on 2007-12-22
Now I have something to work with....

Thank you all very much.:)

---

