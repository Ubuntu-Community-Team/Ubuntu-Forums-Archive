---
title: "Macbook wireless from Ububtu"
date: 2009-07-15
forum: Apple Hardware Users
---

### Post by dePeatrick on 2009-07-15
Hi, I have a Acer Laptop running Ubuntu 9.04 connected via wireless modem to internet and a MacBook connected via Airport to the Acer.
 

 I am finding the Acer(Ubuntu) fine on the internet but am getting very bad speeds on Macbook using Airport.  
 

 I am new to Linux as am normally a Mac user, feel this is merely a configuration issue either on the Mac or on Ubuntu.
 

 Ideally I would like to get the Acer to work as a server for the other two macs I have.
 

 The Acer (Ubuntu) has an Atheros Card -  AR2413 802.11bg NIC

I have had no problems as far as I can tell commecting the MacBook into wireless in other locations so am of a mind that it is an Ubuntu wireless config issue
 

 ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:0a:e4:f6:ca:ea   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:20 Base address:0x3000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:13298 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:13298 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:2606548 (2.6 MB)  TX bytes:2606548 (2.6 MB) 
  
 ppp0      Link encap:Point-to-Point Protocol   
           inet addr:89.204.231.10  P-t-P:10.64.64.64  Mask:255.255.255.255 
           UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1 
           RX packets:31365 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:27793 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:3  
           RX bytes:29877273 (29.8 MB)  TX bytes:4135647 (4.1 MB) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:16:ce:14:b4:ba   
           inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 
           inet6 addr: fe80::216:ceff:fe14:b4ba/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:3022 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:3868 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:406175 (406.1 KB)  TX bytes:3623168 (3.6 MB) 
  
 wmaster0  Link encap:UNSPEC  HWaddr 00-16-CE-14-B4-BA-34-62-00-00-00-00-00-00-00-00   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by dePeatrick on 2009-07-22
Bump...

---

