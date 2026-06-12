---
title: "setting up a static ip address"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-08
Hello!
I'm trying to set up my connection for bittorrent, and to do that, I need to assign a static ip address for my dynamic one. First, I need to know where to find the basic information for my connection. I know in windows there's a simple command to do this, I need to know what to do for ubuntu. Next, I need to know what to do to assign the static ip address based on the information given from the previous question. 
Thank you!

---

### Post by CatKiller on 2006-10-08
```
ifconfig
``` is the equivalent of Windows' ipconfig. You can do most of your network stuff from System -> Administration -> Networking.

---

### Post by blendmaster on 2006-10-08
Okay, well, I need to know which of the following is which:

> 

eth0      Link encap:Ethernet  HWaddr 00:11:2F:BE:A7:D7
          inet addr:70.226.200.36  Bcast:70.226.200.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:febe:a7d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1325613 (1.2 MiB)  TX bytes:238325 (232.7 KiB)
          Interrupt:217 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3096 (3.0 KiB)  TX bytes:3096 (3.0 KiB)



I'm guessing the ip address is 70.226.200.36, the subnet mask is 255.255.255.0, and the gateway address is 70.226.200.255. However, if they are then I'm getting an error, because I can't load pages with these set.

Thanks!

---

### Post by blendmaster on 2006-10-08
By the way, the smily in that code isn't supposed to be there. It just assumed ```
:D
``` meant smily.

---

### Post by NeoGreen on 2006-10-08
Are you trying to setup a static ip within a network?  If you are and you are using a router, you may have to check the configurations in your router.

---

### Post by blendmaster on 2006-10-08
I'm setting it up so I can use p2p clients like bittorrent. I could do it in Windows, but I'm not having any luck with ubuntu.

---

