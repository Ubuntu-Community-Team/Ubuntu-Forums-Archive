---
title: "[SOLVED] How do I find out by 'Internal' IP address?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-27
In Windows it would be 

ipconfig /all

What do I use in Ubuntu?

---

### Post by eentonig on 2007-08-27
It's almost the same
> rfonteyn@gauloises:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:08:02:B5:69:02  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34114519 (32.5 MiB)  TX bytes:8660513 (8.2 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5952 (5.8 KiB)  TX bytes:5952 (5.8 KiB)


---

### Post by chrome307 on 2007-08-27
Thank you it was just what I was looking for :)

---

