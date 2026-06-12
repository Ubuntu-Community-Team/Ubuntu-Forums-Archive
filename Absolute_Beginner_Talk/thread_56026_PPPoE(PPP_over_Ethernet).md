---
title: "PPPoE(PPP over Ethernet)"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by st_tsvetkov on 2005-08-11
How can i set up a PPPoE internet connection? I can't connect to internet.(Point to Point Protocol over Ethernet)

---

### Post by Knome_fan on 2005-08-11
Open a terminal and then type sudo pppoeconf.

Hope this helps.  :grin:

---

### Post by st_tsvetkov on 2005-08-11
Thank you very much Knome_fan. It worked. :smile:

---

### Post by droganov on 2007-05-12
Hi Guys,
I have problems with pppoeconf on Ubuntu Studio.

My provider uses PPP over the LAN. I've set up eth1 to work correctly, but when I run pppoeconf all that I get is that it couldn't find ppp service in my network.

In other systems I have to point ppp service name to 10.0.0.1 but how to do that in Ubuntu?

---

