---
title: "Internet/Network Problem"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by DarkDestroyerNL on 2006-03-16
Hello, I've got some problems with Ubuntu 5.10 with the Internet Connection I have a static Ip connection With a pc with WinXP and my linux pc. I've set up some Ip's one called 192.168.0.228 and my linux pc 192.168.0.229 my pc with internet is connect by a second networkcard with cable to my linux pc 
But I have still no internet connection the kable is good also the wiring to my linux pc is good. but still no sign in winxp network menu of a connection.. 

her is my ifconfig:
eth0
link encap: ethernet  hwaddr 00:01:03:05:c8:89
inet addr: 192.168.0.229 Bcast: 192.168.0.229 mask: 255.255.255.0
inet6 addr: fe80::201:3ff:fed5:c880/64 Scope:link
UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 MiB)  TX bytes:0 (0.0 MiB)
          Interrupt:10 Base address:0xd800
Lo:
Link encap: local loopback
inet addr: 127.0.0.1 mask:255.0.0.0
inet6 addr: ::1/128 Scope:host
UP LOOPBACK RUNNING MTU:16436 Metric: 1
RX packets:14183 errors:0 dropped:0 overruns:0 frame:0
TX packets:14183 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes: 1279412 (1.2 MiB)  TX bytes:1279412 (1.2 MiB)

Can someone solve my problem?:confused:

---

### Post by noswal on 2006-03-16
This is how I did it
[http://ubuntuforums.org/showthread.php?t=141464](http://ubuntuforums.org/showthread.php?t=141464)

---

### Post by OffHand on 2006-03-16
I only see one network card. Your second (eth1?) doesn't show in the ifconfig.

---

