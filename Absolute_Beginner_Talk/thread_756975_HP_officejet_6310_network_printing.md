---
title: "HP officejet 6310 network printing"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2008-04-16
Hi,

the HP officejet 6310 comes with a print server built in, meaning that you can just connect it to your router, and winblows pcs supposedly can connect and print freely...

on ubuntu, will i need to use the hplip GUI to install this, as the printer itself will probably not display on any network?

HPLIP says this: > Network support indicates built-in ethernet and/or wireless networking. Alternatively, many devices may be operated on the network using an external JetDirect print server. Not all network configurations are supported

I'm a bit confused, does this mean i will or won't be able to print? on their 'supported printers' page, it says that they support network printing on the 6310... so... bit confused...

thanks for all your help...

---

### Post by stchman on 2008-04-16
> **benji.ijneb said:**
> Hi,

the HP officejet 6310 comes with a print server built in, meaning that you can just connect it to your router, and winblows pcs supposedly can connect and print freely...

on ubuntu, will i need to use the hplip GUI to install this, as the printer itself will probably not display on any network?

HPLIP says this: 

I'm a bit confused, does this mean i will or won't be able to print? on their 'supported printers' page, it says that they support network printing on the 6310... so... bit confused...

thanks for all your help...

According to openprinting.org the OfficeJet 6300 is supported mostly.  There is no mention of the 6310, but there probably is not that much of a difference in the 6300 vs. the 6310.

[http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_6300](http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_6300)

Now as far as networking it, you will need to assign the printer an IP.  I prefer to assign the printer an IP in the router range but outside the router's DHCP.

Example.

Router IP is 192.168.1.1
DHCP range is 192.168.1.100 to 192.168.1.199 set the printer's IP address to 192.168.1.200.

Tell Ubuntu to install the printer and Ubuntu should find it.

---

### Post by benji.ijneb on 2008-04-16
> **stchman said:**
> According to openprinting.org the OfficeJet 6300 is supported mostly.  There is no mention of the 6310, but there probably is not that much of a difference in the 6300 vs. the 6310.

[http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_6300](http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_6300)

Now as far as networking it, you will need to assign the printer an IP.  I prefer to assign the printer an IP in the router range but outside the router's DHCP.

Example.

Router IP is 192.168.1.1
DHCP range is 192.168.1.100 to 192.168.1.199 set the printer's IP address to 192.168.1.200.

Tell Ubuntu to install the printer and Ubuntu should find it.

thanks,

how do i assign it an ip, and how do i tell ubuntu to find it? (i'm a bit of a noob)

also, i have an ip address that's constantly changinc (i think that's called a static ip - i'm not sure) won't that make things difficult...?

---

### Post by drsox1899 on 2008-04-26
Hi there.  I have one of these and have just moved over from WinXp to Ubuntu 7.

First, some questions for you.

0.  How is the HP6310 connected ?  If it is by USB to a PC then what follows is not much help.  If it is by wired ethernet, then read on.

1. How do you connect your PC to the internal network ?  Do you have a Router (might be the same box that connects to the Internet - DSL or Cable) ?

2. How do you get IP addresses for your PC - from the Router or by setting them to fixed addresses ?  From the Router will usually be called DHCP (mostly), fixed are Static.

3.  If you can and a Router exists, go into the Router setup screens with a Web Browser (Firefox) and see if you can find the DHCP clients list. (If it exists).  On that list you might find the IP address of your HP 6310.

4. If you find it (e.g. 192.168.123.22), then type this into a new Firefox tab and you will be connected to the internal server of the HP 6310.

5. From than you can then setup whatever you want.

6.  PS I am also assuming that the HP6310 is connected by wired ethernet to your router - if it isn't, then see if you can connect it.  Do a reset on the HP 6310 and you should be able to have it find the Router.

7. PPS Of course if you still have a Win PC then running setup in the HP software will allow you to do all this easily - but I'm assuming you don't.

):P


Oh by the way, there are no problems with using the HP6310 in Ubuntu.  It usually gets recognised automatically and installs the right driver. !!

---

### Post by wheezer on 2008-05-22
> 
Oh by the way, there are no problems with using the HP6310 in Ubuntu.  It usually gets recognised automatically and installs the right driver. !!

This is the first HP all in one i can find where someone says they got it to run under Feisty.  So do I push the button on this, and order it? Egghead has a good price.  Would love to hear someone endorse it ;)

Thanks

---

