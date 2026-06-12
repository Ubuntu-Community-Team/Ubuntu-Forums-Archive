---
title: "How to Detect Newtork Card"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by mvyvoda on 2006-04-27
i can't see my network card (Linksys WMP54GR) in the network settings. Can someone suggest a starting point please?

Thanks, 
Mark
mvyvoda [AT] gmail [DOT] com

---

### Post by carlexpc on 2006-04-27
try typing **ifconfig -a** on your command line to see all the NIC installed on your pc.

---

### Post by mvyvoda on 2006-04-27
when i type that i get: 
```
eth0      Link encap:Ethernet  HWaddr 00:D0:09:FB:0E:47
          inet6 addr: fe80::2d0:9ff:fefb:e47/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:47851 (46.7 KiB)  TX bytes:47851 (46.7 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

i have two ethernet cards. the one i need to work is the wireless one, and that doesn't appear to be detected.

what next?

thanks for your time and energy!, 
-m

---

### Post by Bleachedbluejeans on 2006-04-27
I am a noob, but I managed to get some good links into my signature lines that may help! (See below):D

LMAO! I'll try logging in as myself, rather than as my wife first, then I'll post...

---

### Post by Papa-san on 2006-04-27
This ought to work a little better...

:rolleyes:

---

### Post by mvyvoda on 2006-04-27
awesome, thanks papa. those are good links, i'll start there. btw, does anyone know if that "sit0" my wireless card?

thanks, 
-m

---

