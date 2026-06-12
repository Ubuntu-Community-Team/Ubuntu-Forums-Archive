---
title: "kismet dropping priveliges config chaos!"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by adza on 2008-03-04
Hi there, i've edited the kismet.conf file to add the line > suiduser=adza however i still get the error message > FATAL:  Could not find user 'your_user_here' for dropping priviledges.  Make sure you have a valid user set for 'suiduser' in your config file.  See the 'Installation & Security' and 'Configuration' sections of the README file for more information.
 when i'm trying to start kismet.. is there another conf file i need to edit? 

And one more thing... here is my ifconfig > eth0      Link encap:Ethernet  HWaddr 00:15:C5:39:17:E0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:A5:99:26  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fea5:9926/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19556 errors:7 dropped:5166 overruns:0 frame:0
          TX packets:13657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16826804 (16.0 MB)  TX bytes:2093763 (1.9 MB)
          Interrupt:17 Base address:0x2000 Memory:dfdff000-dfdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12325 (12.0 KB)  TX bytes:12325 (12.0 KB)


what should the source line in the .conf file be as well????

---

