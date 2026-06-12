---
title: "Kubuntu/Mint KDE: Internet Sharing"
date: 2012-09-28
forum: Any Other OS
---

### Post by cain071546 on 2012-09-28
i am using my neighbors wifi.
i would like to share Internet  (wlan0) through my NIC (eth0) to a router then to my windows PCs.

i do not have a crossover cable.

network-manager--->manage-connections-->wired/wireless tab-->add-->(either wired/wireless/shared-->

i get lost when setting ipv4 settings it lists
shared,(auto DHCP-i know what that means)manual,link-only
i have tried DHCP,shared,link-only and setting the IP manually with no luck 

I have been unsuccessful in sharing the connection thus far 

this is output of (ifconfig)

eth0      Link encap:Ethernet  HWaddr 8c:89:a5:2c:bd:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8797 (8.7 KB)  TX bytes:8797 (8.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:88:f5:3f:bd  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fef5:3fbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:764606 (764.6 KB)  TX bytes:128783 (128.7 KB)

i have no idea where im going wrong here

---

### Post by bionaught on 2012-12-24
Did you ever find a solution.
I want to do exactly the same thing. But also get lost in a lot of the tech details
cheers bio

---

