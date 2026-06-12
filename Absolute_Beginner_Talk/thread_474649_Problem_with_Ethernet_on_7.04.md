---
title: "Problem with Ethernet on 7.04"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by sachill on 2007-06-15
Ive just updated from Ubuntu 5.04 to 7.04.  On the old edition I could connect to the internet (DSL connection). Now, after doing the same network configurations I did then, I cant connect on 7.04  Please help.

---

### Post by sachill on 2007-06-15
I just ran ifconfig, and this is what I get:

eth0      Link encap:Ethernet  HWaddr 00:08:74:9D:00:BD   
          inet6 addr: fe80::208:74ff:fe9d:bd/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:14868 (14.5 KiB)  TX bytes:23158 (22.6 KiB) 
          Interrupt:11 Base address:0xec00  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1336 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1336 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:102928 (100.5 KiB)  TX bytes:102928 (100.5 KiB)

---

### Post by HereInOz on 2007-06-15
You are clearly not getting an IP address assigned by your DHCP server, which is probably your router.  

Go into System > Administration > Network, open the properties of the eth0 connection, and make sure that you have roaming mode enabled.

If that doesn't help, try setting a static IP, with the gateway address that of your router, and set your DNS addresses to those provided by your ISP.

Check the roaming mode first though.

---

### Post by sachill on 2007-06-15
sorry, how do I check the DNS addresses on my other laptop on the network, which has the internet working and runs on XP?  I can type these DNSs into my ubuntu network settings?

in any case, each time I enable roaming mode, all the Connection Settings get greyed out and I cant select anything.  Im starting to think that updating to 7.04 was not the best move...

---

