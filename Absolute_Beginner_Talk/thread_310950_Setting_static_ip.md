---
title: "Setting static ip"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-12-02
I have WRT54G. How to set a static IP? What IP should I use for the gateway?

IP Address : 192.168.1.111
Subnet Mask: 255.255.255.0
Gateway    : 192.168.1.100

This settings make me can't go to internet.:(

---

### Post by biffta on 2006-12-02
Sorry but what? Are you asking how to configure you WRT54G router? This is not the place for doing so.

---

### Post by oliviacond on 2006-12-02
I'm not, ok. I just want to set up a static IP on my pc based on the router. Different router has different kind of IP.
This is the information of my network:

> 
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:B5:52:4D  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:feb5:524d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21687029 (20.6 MiB)  TX bytes:2153463 (2.0 MiB)
          Interrupt:185 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

> 
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         DD-WRT          0.0.0.0         UG    0      0        0 eth0

> 
~$ cat /etc/resolv.conf
nameserver 192.168.1.1


---

### Post by CatKiller on 2006-12-02
> **oliviacond said:**
> How to set a static IP?

System -> Administration -> Networking -> Select your network card -> Properties -> Configuration

You'll want to set an IP address that is outside of the range of addresses assigned by the router. For example, my router hands out addresses starting at 192.168.1.100, and the static IP address I've chosen for this computer is 192.168.1.3.

> What IP should I use for the gateway?

The IP address of your router. This may well be 192.168.1.1.

You might find more specific information in the Networking forum.

---

### Post by oliviacond on 2006-12-02
problem solved. thanks. :)

---

### Post by bionnaki on 2006-12-02
off-topic...

I recommend [http://www.thibor.co.uk](http://www.thibor.co.uk) if your router is supported.

---

