---
title: "DNS, DHCP aaarrrrrgggghhhhh"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Simpleton on 2007-01-03
Hi,

This is my first post as I am a little bit of a newbie to all this, please excuse my general stupidity!

The problem I have appear to be with DNS.

My setup:
Netgear Router (settings correct for BT)
6.06
DHCP network

The net seems uber-slow all the time to load pages. I think that the problem is the DNS. I have done the etc/resolv.conf thing to change it to 4.2.2.1 & 4.2.2.2. This actually allows me to surf the web. I have also altered the sudo nano /etc/dhcp3/dhclient.conf and removed the line before Host Name. This seems to allow me to access the web without keep entering the DNS all the time.

However it is still really really slow! I have also changed the setting of Ipv6 to true. However, when I open Firefox, it seems slow in loading Google as a home page.

Please can anybody help a non-techie????

Mark.

---

### Post by Bachstelze on 2007-01-03
You need to know what the adresses of your ISP's DNS servers are - just google for it - and put them in /etc/resolv.conf and you should be fine :)

---

### Post by Simpleton on 2007-01-03
Can't seem to find them, sorry.

---

### Post by bmt on 2007-01-03
I can recommend the [OpenDNS]("http://www.opendns.com") service -- full information on their website, with instructions for adding the DNS server IPs to the router.

However, you may be suffering other slow downs -- many threads on here already: [this one]("http://www.ubuntuforums.org/showthread.php?t=328747&highlight=slow+dns") is recent and holds my attention ...

---

### Post by pross on 2007-01-03
assuming your with BT in the UK...

the DNS servers according to my netgear router are:
Domain Name Server  	194.74.65.69
                                            194.72.9.34

hope it helps

---

### Post by r4ik on 2007-01-03
Here is a read just might help,

[http://www.ubuntuforums.org/showthread.php?t=330189](http://www.ubuntuforums.org/showthread.php?t=330189)

Good luck !

---

