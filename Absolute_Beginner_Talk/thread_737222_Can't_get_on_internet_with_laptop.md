---
title: "Can't get on internet with laptop"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by huntis619 on 2008-03-27
I have a hpzv5410us laptop. I can get on the internet using wireless but when I plug up my ethernet cable I can't get on the internet. I've tried different ethernet cables still nothing. Please help

---

### Post by opscure on 2008-03-27
what do you get when you enter ```
ifconfig -a
```in terminal?

Have you tried configuring your network with DHCP?
Applications->System->Network
click on your network adapter and click properties
uncheck roaming mode and use the configuration pulldown to DHCP
press ok and check the little checkbox next to your Wired Connection
press close and try your connection again

---

### Post by huntis619 on 2008-03-27
when I typed in ifconfig -a in the terminal this what it saysifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:4C:8F:1B  
          inet6 addr: fe80::20f:b0ff:fe4c:8f1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:17 Base address:0x2800 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:A8:C7:7E  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41143803 (39.2 MB)  TX bytes:1828198 (1.7 MB)
          Interrupt:22 Memory:e0104000-e0106000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5248 (5.1 KB)  TX bytes:5248 (5.1 KB)

Also I tried what you said and it didn't work.

---

