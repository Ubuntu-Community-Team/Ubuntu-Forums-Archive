---
title: "not new to computers but linux is like dos 5"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by jimbean on 2006-11-24
--------------------------------------------------------------------------------

 ive installed ubuntu and have no internet
ive installed kubuntu and it works fine {internet}
ive tried [sudo pppoeconf and it will not configure anything
ive tried [sudo ifconfig and got this

eth0 Link encap:Ethernet HWaddr 00:01:29:21:53:AC 
inet addr:10.0.0.4 Bcast:10.0.0.255 Mask:255.255.255.0
inet6 addr: fe80::201:29ff:fe21:53ac/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:3122 (3.0 KiB) TX bytes:5889 (5.7 KiB)
Interrupt:10 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:40 errors:0 dropped:0 overruns:0 frame:0
TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:2950 (2.8 KiB) TX bytes:2950 (2.8 KiB)

ive checked my network settings and it has the wired internet connection checked and is set to automatic config

ive had some internet activity buy fooling around with stuff i did not know 
and it,, letsay connected but it did not finish the web page and it took a long time for that

---

### Post by IYY on 2006-11-24
Is your wired connection set to DHCP?

---

### Post by jimbean on 2006-11-24
fixed it it was fire fox 
thanks anyway

---

### Post by mossyjaw on 2006-11-24
I'm having similar difficulty.  Just how did you fix it?

---

### Post by jimbean on 2007-03-06
i disabled ipv6 in firefox
typed in about:config in address bar in firefox
and set to true or false which ever was the case

---

