---
title: "[SOLVED] Ip question."
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-21
Hi there,

Stupid question, how do I find out my internal IP adress? I am behind a router and when I run ifconfig, I get the external adress there but what about the internal one? Cheers.

---

### Post by wormser on 2008-03-21
That should be your internal IP when running ifconfig.  Go to [www.whatismyip.com](www.whatismyip.com) and compare the two.  Depending on your router, your internal should start with 192.168.x.x.

---

### Post by lover_of_sc on 2008-03-21
Thats what I thought as well, i cant find a number even close to that:

eth0      Link encap:Ethernet  HWaddr 00:1B:24:AD:2C:1D  
          inet addr:86.52.184.49  Bcast:86.52.185.255  Mask:255.255.254.0
          inet6 addr: fe80::21b:24ff:fead:2c1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115629500 (110.2 MB)  TX bytes:68290919 (65.1 MB)
          Interrupt:17 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39107 (38.1 KB)  TX bytes:39107 (38.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:DB:B9:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Any ideas mate?

---

### Post by Dr Small on 2008-03-21
That is the results of your internal IP addresses. Are you behind a router?

---

### Post by wormser on 2008-03-21
What type of router do you have and who is the service provider?  If you are on cable internet typically they give you a cable modem and not a router.  In that case your external will be the same as ifconfig.

---

### Post by lover_of_sc on 2008-03-21
Currently at my girlfriend, have a router at home - appears like she only have a cable modem and not a router, Silly me! :-)

---

### Post by wormser on 2008-03-21
> **lover_of_sc said:**
> Currently at my girlfriend, have a router at home - appears like she only have a cable modem and not a router, Silly me! :-)

Well, get a router there for better security.

---

### Post by lover_of_sc on 2008-03-21
Yes, that sounds like a wise plan. Cheers for your help.

---

