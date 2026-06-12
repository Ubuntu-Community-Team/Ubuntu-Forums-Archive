---
title: "Question about hardware and drivers..."
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by anubisx on 2006-03-09
first off, hi! just recently installed ubuntu on an old compaq laptop. at first we didnt think it had a working ethernet port, but my friend oj found one hidden behind this little square. now I tried it last nite, but it didnt connect to my network. do I need to install seperate drivers? or should I just go and buy a wireless card? I want to use as little money as I can on this laptop.

---

### Post by Brunellus on 2006-03-09
can you post what model laptop it is?  Should be printed somewhere near the serial number (underside of the unit).  

when you open up a terminal and type

ifconfig -a

what is the output?  (copy the EXACT output here--don't summarize).  If you see anything like 

eth0

anywhere in that output, you probably have an etherent connection that's already detected.  You should be able to bring the interface up and online using the Network Settings GUI, or we can show you how to do it via the commandline.

---

### Post by anubisx on 2006-03-09
alrite the laptop model is Compaq Presario 1690.
the output from the terminal is:

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: :1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:3480 errors:0 dropped:0 overruns:0 frame:0
       TX packets:3480 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       Rx bytes:273961 (267.5 KiB)  TX bytes:273961 (267.5 KiB)

sit0  Link encap:IPv6-in-IPv4
       NOARP MTU:1480 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

thats what I got after I put in ifconfig -a.

do you think I might have to open it up and connect something to the port?

---

