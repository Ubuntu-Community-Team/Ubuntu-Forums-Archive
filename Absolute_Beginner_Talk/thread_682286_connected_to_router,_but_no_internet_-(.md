---
title: "connected to router, but no internet :-("
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by corevette on 2008-01-29
```
corevette@corevette-desktop:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:F8:1C:1E  
          inet addr:172.16.1.39  Bcast:172.16.255.255  Mask:255.255.0.0 
          inet6 addr: fe80::20f:b5ff:fef8:1c1e/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:892 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:329 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:73547 (71.8 KB)  TX bytes:45871 (44.7 KB) 

eth0      Link encap:Ethernet  HWaddr 00:40:CA:87:FE:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5320 (5.1 KB)  TX bytes:5320 (5.1 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-F8-1C-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:26790 errors:0 dropped:0 overruns:0 frame:3532 
          TX packets:883 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:1984138 (1.8 MB)  TX bytes:77627 (75.8 KB) 
          Interrupt:19 

```

```
corevette@corevette-desktop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0 
172.16.0.0      0.0.0.0         255.255.0.0     U     0      0        0 ath0 
0.0.0.0         172.16.0.1      0.0.0.0         UG    0      0        0 ath0 
```

```
corevette@corevette-desktop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
```
i turned on the computer one day and my Netgear WG311t doesn't work

---

### Post by RedBird on 2008-01-29
Did you check your router connection status not from Ubuntu but from the router built-in configuration menu?

---

### Post by corevette on 2008-01-30
yes i tried that

---

### Post by candtalan on 2008-01-30
Does the router  itself report that it is transferring to and from the ISP then?

---

### Post by corevette on 2008-01-30
> **candtalan said:**
> Does the router  itself report that it is transferring to and from the ISP then?
how do i tell? also, i tried using a static IP and still no avail.  don't know where to go now :(

---

### Post by kathmary on 2008-01-30
Just an idea, but are you booting windows from another drive?  If so it might help to change windows settings for the network card.  I had this problem...and I had to enable "Wake-On-Lan After Shutdown" under the advanced tab in the properties of the network card in hardware manager for xp.

---

### Post by xzero1 on 2008-01-30
Check and see if the router has ip release and renew. Set the router for an automatic configuration . For most internet connections the router needs a static or assigned ip address, internet gateway address and dns address.

---

### Post by candtalan on 2008-01-30
adsl modem/router online?
> **corevette said:**
> how do i tell? also, i tried using a static IP and still no avail.  don't know where to go now :(
your router is very likely to have a web-page-like information page which you hopefully can access by using a browser with
172.16.0.1    (if I read your initial information correctly)
as the address. The information page/s will include a router status - something like offline/showtime and you will see numbers of transferred bytes refreshed to increasing totals.

---

