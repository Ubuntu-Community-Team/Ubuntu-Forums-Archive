---
title: "Ubuntu 5.10 ADSL connection problem"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by jaccuse on 2006-05-05
Hi all.  I have a speedstream 4200 modem with usb connection and cannot connect to my optus (Australia) ADSL account.  I have tried:
1. Disabling ipv6 in firefox and editing /ec/modprobe.d/aliases. I typed in alias net-pf-10-off #ipv6, saved and rebooted.  When this didn't work I undid these and started again
2. Entering nameserver 211.29.133.126 nameserver 66.36.241.109 in the dns tab in networking and checking that these entries are in /etc/resolv.conf.  I then commented out a section of /etc/dhcp3/dhclient-script as recommended in ubuntu forums.
3. entering a static ip address.
4. Using ppoeconf. Got access concentrator problem, posted, no response so tried all of the above
eth0 is listed as active.
I am getting nothing in GAIM or firefox, or synaptic
These ideas I got from searching ubuntu forums. Alas
none of them have worked.  Any ubuntu users out there with any ideas?

---

### Post by richbarna on 2006-05-05
Hi, Your problem is the usb connection.
I spent a long time a couple of years ago researching how to get a usb modem working on Linux (Forums are full of thousnds of posts), in the end you realise that it is cheaper, easier to just get a router.
The config is so easy it is unbelievable.
As for cost, I got a second hand 4 port router for 30 bucks.

---

### Post by jaccuse on 2006-05-05
Fantastic. I have no problems buying a router, just didn't know that was the solution.  Thank you, wish I'd asked earlier.

---

### Post by 3rdalbum on 2006-05-05
...an ADSL modem/router, not a regular Ethernet router. Make sure you've got a spare Ethernet port too.

---

### Post by jaccuse on 2006-05-05
I've made a mistake. my modem is connected via ethernet cable to motherboard.  I've just added a network card and now have eth0 and eth2 active.  Still no internet response.  Will buy a router if still needed. Any other suggestions?

---

