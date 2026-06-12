---
title: "Weird Network Problem"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-09-09
This happens every time, I'm on my laptop with a braodcom 1390 wireless card, something comes up and I have to temporarily put it it standby.  When I resume, like it should do, it reconnect to the network.  When it does, it says that its connected to a wired network. 

It works fine I can surf the web ok, but I don't have any signal information.  I have tried to reconnect several times, it always says that its a wired network, I have no clue on what's going on. 

   Thanks for your future help!

---

### Post by finer recliner on 2007-09-10
post the output from the command, ifconfig

---

### Post by Xorg.conF on 2007-09-10
ok here it is:

eth0      Link encap:Ethernet  HWaddr 00:14:22:98:AF:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:96:20:A5  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2121813 (2.0 MiB)  TX bytes:211440 (206.4 KiB)
          Interrupt:17 Memory:dfdfc000-dfe00000 

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:98:AF:00  
          inet addr:169.254.4.221  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:529 (529.0 b)  TX bytes:529 (529.0 b)

---

### Post by finer recliner on 2007-09-10
hmm we'll you're definitely connect via you're wireless card. i dont know why it thinks its a wired connection. sorry i cant help more.

---

