---
title: "Mostly internet connection problems"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by nhi on 2007-04-17
Hey i've just started to use ubuntu and ihave a problem, internet connection problem I was told yesterday to post my ifconfig so one of the other ubuntu's will help me to recognize the problem, however the sympthoms are that the web browser stop loading new websites after a while and new downloads does seem to start however downloads at the middle of the process continue :confused: 
any idea what's the problem? 

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:18:F3:BD:60:F2  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:febd:60f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7807476 (7.4 MiB)  TX bytes:1437514 (1.3 MiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3353 (3.2 KiB)  TX bytes:3353 (3.2 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:82.81.166.242  P-t-P:82.81.166.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:893688 (872.7 KiB)  TX bytes:226247 (220.9 KiB)

---

### Post by H.E. Pennypacker on 2007-04-17
I highly recommend you separate your two problems.  This is much better for the messageboard.

As for your printer issue, linuxprinting.org reports the printer works perfectly, which is odd, because Lexmark printers can be hassle on Linux.  Anyhow, doing a forum search, I was able to find a guide on how to get this printer to work (it's not really a guide - it's a few steps):

[http://ubuntuforums.org/showthread.php?t=275138&highlight=lexmark+e120](http://ubuntuforums.org/showthread.php?t=275138&highlight=lexmark+e120)

I did a search on "Lexmark E120," and found that thread in less than a minute.

---

### Post by nhi on 2007-04-17
I have already tried this guide, ubuntu doesn't RECOGNIZE, my printer... doesn't recognize that it is connected
Anyhow i will split my message

---

