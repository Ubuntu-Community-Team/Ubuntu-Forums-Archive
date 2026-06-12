---
title: "internet problems in fiesty"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by tigz on 2007-12-12
I have just installed ubuntu 7.04 fiesty on my desktop. I am running a dual boot (ubuntu is booting from [wubi]("http://wubi-installer.org/")) with windows vista as my main OS. I am using a WIRED FIOS (fiber optics) verizon actiontec router that is hooked up to two other computers, one of which hooks in wirelessly. When I boot into vista, my internet works fine. When I boot into ubuntu however, it does not work at all. I previously was using a Netgear (WGR614 v6) router and had the exact same problem. 

Here is a copy of the ifconig that I ran from terminal

```
sasha@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:E7:99:99  
          inet6 addr: fe80::20c:6eff:fee7:9999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xa800 

eth0:avah Link encap:Ethernet  HWaddr 00:0C:6E:E7:99:99  
          inet addr:169.254.8.255  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97616 (95.3 KiB)  TX bytes:97616 (95.3 KiB)
```

please help!

---

### Post by pwaldo on 2007-12-13
Are you trying to connect with an ethernet cable or a wireless card?

---

### Post by lenswipe on 2007-12-13
> **pwaldo said:**
> Are you trying to connect with an ethernet cable or a wireless card?

he just said hes trying to connect with a fibre-optic  card which is neither ethernet now wireless.... :P

---

