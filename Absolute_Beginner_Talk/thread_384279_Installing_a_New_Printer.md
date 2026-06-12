---
title: "Installing a New Printer"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-14
I'm trying to install a HP 3600n Color Laserjet. It is connected to the computer via a DSL modem/4 port hub -- Computer -> Hub -> Printer -- essentially NIC to NIC. There is no domain. The MAC address for the printer is 192.168.1.4. I have downloaded / installed the appropriate driver (hplip-1.7.2.run).

In the Add a Printer wizard there are several options for network printers:
CUPS printer (which asks for a URI)
Windows Printer (which wants to know the host and printer)
Unix Printer (asking for Host and Queue)
HP JetDirect (wants Host and Port)

If I select "Local Printer" I'm told there is no device found (it wants LPT1, or 1 of 2 parallel ports).

Since I'm connected NIC to NIC and that option is not listed in the local printer type, what do I do?

---

### Post by andreas64 on 2007-03-14
Hi,

open a terminal and type 'hp-makeuri 192.168.1.4'

This generates the needed URI for CUPS.

Andreas

---

### Post by tgalati4 on 2007-03-14
In a browser:

localhost:631

Linux uses CUPS as its printing engine.  If you search CUPS in the forums you will find a number of tutorials on how to troubleshoot printers.

Good luck.

---

### Post by lwalper on 2007-03-14
OK. Did the 'hp-makeuri 192.168.1.4' --- all went as planned. Then added a printer (the appropriate one) and sent a print job to the printer. No joy.

The print job is in the que, but seems to be having trouble finding the printer. Let me go read some CUPS forums.

---

### Post by dstew on 2007-03-14
Sometimes you have to start the printer. In the CUPS manager, look for a Start Printer button.

---

### Post by stchman on 2007-03-14
> **lwalper said:**
> I'm trying to install a HP 3600n Color Laserjet. It is connected to the computer via a DSL modem/4 port hub -- Computer -> Hub -> Printer -- essentially NIC to NIC. There is no domain. The MAC address for the printer is 192.168.1.4. I have downloaded / installed the appropriate driver (hplip-1.7.2.run).

In the Add a Printer wizard there are several options for network printers:
CUPS printer (which asks for a URI)
Windows Printer (which wants to know the host and printer)
Unix Printer (asking for Host and Queue)
HP JetDirect (wants Host and Port)

If I select "Local Printer" I'm told there is no device found (it wants LPT1, or 1 of 2 parallel ports).

Since I'm connected NIC to NIC and that option is not listed in the local printer type, what do I do?

First off don't use a hub you NEED a router.  Does your DSL modem have a built in router?  A router is capable of IP generation for what you need.  Hubs or switches do not assign IPs.  Routers are really cheap ($25 or so) and also allow you to share your internet connection.

Second when you use a router there is usually a specified range like 192.168.1.100 to .200 for example.  Since you are specifying an IP put it in the upper range like for the example IPs I have select 192.168.1.199.  You can modify your printer's IP through a web browser or the front panel.

Third use th HP JetDirect selection and leave the port at it's default (9100 I believe) and put your new IP 192.168.1.199 in the Host section.  Select your printer driver and it will work.  I have an HP Laserjet 4050tn and a 2605dn and they both work EXCELLENT.

---

### Post by lwalper on 2007-03-15
stchman,

I said hub, but it's a modem/router (Comtrend ADSL2+ Router). I'll try your suggestions. So far I've not gotten any printer output.

Thx

---

### Post by stchman on 2007-03-15
> **lwalper said:**
> stchman,

I said hub, but it's a modem/router (Comtrend ADSL2+ Router). I'll try your suggestions. So far I've not gotten any printer output.

Thx

So it is a DSL modem with built in router.  You will need to determine the IP range of the router.  You can probably get into the router's software via 192.168.1.1 and then see what the range is.  Your router might deal with 192.168.0.xxx ip ranges in that case you will need to change your printer's IP.

Trust me, what I have laid out works.

---

### Post by lwalper on 2007-03-15
What I did was :

In the printer properties, changed from CUPS to HP JetDirect; put the IP address (192.168.1.4) in the host section; printed a test page --- presto --- it prints.


Thanks for your help!!!

---

