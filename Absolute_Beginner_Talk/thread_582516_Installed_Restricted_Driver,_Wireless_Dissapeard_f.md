---
title: "Installed Restricted Driver, Wireless Dissapeard from Network Manager"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nglatt on 2007-10-19
Hello,

I installed for the first time about 10 hours ago - went right to 7.10.
Sorry if this question has an easy answer, but I've poured over the forums for the past four hours to even get to this stage. I'm starting to run out of steam.

I just finally figured out how to install the Firmware for Broadcom 43xx. I rebooted. However, the 'wireless' connection is no longer an option in Network Manager. How can I get it to reappear?

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:36:89:29  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe36:8929/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1261 errors:2 dropped:2 overruns:0 frame:0
          TX packets:989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1351543 (1.2 MB)  TX bytes:119507 (116.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



This seems like something easy enough to solve, but I'm about to throw in the towel. Thank you for your time.

---

