---
title: "x41 network/wireless doesn't work"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by newbie1122 on 2007-08-31
i just installed ubuntu 6.10 on my x41 tablet pc, and im having problem with network/wire and wireless.
problem is that i can't connect to network/internet. when i go into connection properties; under general tab i can't change the connection to anyother than "lo". i also try installing the drivers for ethernet and wireless device, but i'm not i did it right. do i even need install driver in ubuntu??

this is what i get from typing ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:23:9F:58  
          inet6 addr: fe80::216:d3ff:fe23:9f58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25665 (25.0 KiB)  TX bytes:32670 (31.9 KiB)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:78:1E:CF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0xe000 Memory:a0202000-a0202fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24308 (23.7 KiB)  TX bytes:24308 (23.7 KiB)

i think eth0 is wire and eth1 is wireless.

this site shows the hardware for x41
[http://www.thinkwiki.org/wiki/Category:X41_Tablet](http://www.thinkwiki.org/wiki/Category:X41_Tablet)


i appreciate any help/comment, plz help

---

### Post by shearn89 on 2007-09-04
Okay - open a terminal and type "lspci" and "iwconfig", and post that here. That should show all connected pci cards, and any interfaces with a wireless extension.

---

