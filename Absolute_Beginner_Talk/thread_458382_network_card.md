---
title: "network card"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by moonliter on 2007-05-29
please can someone help me how can I see which internet network card I use in ubuntu.I need that because windows xp didn't found my network card Help

---

### Post by Kobalt on 2007-05-29
You can see it with the command line *ifconfig*

---

### Post by moonliter on 2007-05-29
I got this information when I type if config :

eth0      Link encap:Ethernet  HWaddr 00:0F:EA:74:76:9F  
          inet addr:10.10.0.220  Bcast:10.10.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:eaff:fe74:769f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12630907 (12.0 MiB)  TX bytes:806427 (787.5 KiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:461 (461.0 b)  TX bytes:461 (461.0 b)

which network card am I using now? Help

---

### Post by simon303 on 2007-05-29
i dont know much about this myself, but the top one is the ethernet card
try ```
lspci
```
it lists all the cards (eg ethernet card, graphics card, sound card) in your pci slots
try looking for any mention of ethernet to work out exactly what your ethernet card is

---

### Post by moonliter on 2007-05-29
Thanks for help!!!

---

