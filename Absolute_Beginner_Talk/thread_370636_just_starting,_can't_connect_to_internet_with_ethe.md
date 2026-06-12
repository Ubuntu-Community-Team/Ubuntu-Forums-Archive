---
title: "just starting, can't connect to internet with ethernet"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-02-25
I just installed ubuntu 5.10 on an old computer, Compaq 1800T.  The only OS on this machine is now ubuntu.  I'm trying unsuccessfully to connect to the internet.  I'm on an LAN going through a router.  I have activated etho1.  Configured using DHCP.   In reading other posts I thought i'd better try ifconfig in the terminal to give the info for help.  Here is the reading:

eth0

Link encap:Ethernet   HWaddr 00:02:A5:A4:3F:E7
inet addr: 192.168.1.5     Bcast: 192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::202:a5ff:fea4:3fe7/64 Scope:Link
UP BROADCAST MULTICAST   MTU:1500  Metric:1
RX packets:14  errors:0  dropped:0  overruns:0  frame:0
TX packets:15 errors:0  dropped:0  overruns:0  carrier:0
collisions:0  txqueuelen:1000
RX bytes:2350  (2.2 KiB)   TX bytes:1701  (1.6 KiB)

lo

Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING   MTU:16436  Metric:1
RX packets:21011 errors:0  dropped:0  overruns:0  frame:0
TX packets:21011 errors:0  dropped:0  overruns:0  carrier:0
collisions:0  txqueuelen:0
RX bytes:1605678  (1.5 MiB)  TX bytes:1605678  (1.5 MiB)

I had to type this in so I hope I got it right.

Where do I go from here?  Thanks.

---

### Post by dcstar on 2007-02-25
> **sagesparrow said:**
> I just installed ubuntu 5.10 on an old computer, Compaq 1800T.  The only OS on this machine is now ubuntu.  I'm trying unsuccessfully to connect to the internet.  I'm on an LAN going through a router.  I have activated etho1.  Configured using DHCP.   In reading other posts I thought i'd better try ifconfig in the terminal to give the info for help.  Here is the reading:

eth0

Link encap:Ethernet   HWaddr 00:02:A5:A4:3F:E7
inet addr: **192.168.1.5**     Bcast: 192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::202:a5ff:fea4:3fe7/64 Scope:Link
UP BROADCAST MULTICAST   MTU:1500  Metric:1
RX packets:14  errors:0  dropped:0  overruns:0  frame:0
TX packets:15 errors:0  dropped:0  overruns:0  carrier:0
collisions:0  txqueuelen:1000
RX bytes:2350  (2.2 KiB)   TX bytes:1701  (1.6 KiB)
......
I had to type this in so I hope I got it right.

Where do I go from here?  Thanks.

It seems to have an IP address, so that would imply it is picking up the DHCP correctly.

What does:
```
netstat -n
``` show?, or:
```
traceroute www.ubuntuforums.org
```

---

### Post by sagesparrow on 2007-02-25
sorry for appearing totally clueless, but when you write "code", what do you mean?  using the terminal?

---

### Post by undertakingyou on 2007-02-25
Yep, he is meaning the terminal.  Really the terminal is quite easy.  I would be curious about a DNS issue because everything else seems to be straight.  That is what dcstar is trying to find.

---

### Post by sagesparrow on 2007-02-26
netstat -n yields a long list of lines that start with "unix".  Everything says either "connected" or is blank in the 4th or 5th column (depending on how you count).

---

### Post by sagesparrow on 2007-02-26
under DNS tab on network settings, 2 DNS server addresses are listed

---

### Post by sagesparrow on 2007-02-26
typing traceroute [www.ubuntuforums.org](www.ubuntuforums.org) yields bash: traceroute: command not found

(so probably i wasn't supposed to type that into the terminal)

---

### Post by sagesparrow on 2007-02-26
OK, now it is working.

---

