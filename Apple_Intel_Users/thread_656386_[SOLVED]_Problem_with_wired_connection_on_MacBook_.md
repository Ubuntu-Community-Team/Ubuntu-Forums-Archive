---
title: "[SOLVED] Problem with wired connection on MacBook Pro"
date: 2008-01-02
forum: Apple Intel Users
---

### Post by gurdy on 2008-01-02
I can't get the wired network connection to work on my MacBook Pro under Ubuntu 7.10.

My MacBook Pro is a generation 1 - Core Duo, and I've installed Ubuntu 7.10 on it in a dual boot configuration with Mac OSX  10.4 , and I've connected the MacBook Pro via ethernet to my home network. In System>Administration>Network I've configured the wired connection with a static IP address (192.168.0.111). 

The same settings for IP address, subnet mask, gateway address, and DNS servers work fine on the MacBook Pro when I boot into Mac OS X. I have another GNU/Linux computer at 192.168.0.1 that is acting as a router to my cable modem connection, and that is all working fine for other computers on my home network.

Any suggestions?

In case this is useful, here's what I get from /sbin/ifconfig (I think -- I typed this in by hand since I have no network connection to the MacBook):

eth0      Link encap:Ethernet  HWaddr 00:16:CB:85:3A:A0  
          inet6 addr: fe80::216:cbff:fe85:3aa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25580 (25.2 KB)  TX bytes:7062 (6.8 KB)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89584 (87.4 KB)  TX bytes:89584 (87.4 KB)

---

### Post by gurdy on 2008-01-02
I rebooted again, and now everything works. I don't what the problem was, but at least it's working now.

---

### Post by cyberdork33 on 2008-01-02
please mark as solved.

---

### Post by gurdy on 2008-01-02
> **cyberdork33 said:**
> please mark as solved.

How do I do that? This is probably a dumb question, but I searched the Forum Help and still don't have a clue how to do that.. I tried editing the first post and adding [SOLVED] to its title, but that didn't show up in the list of threads.

---

### Post by cyberdork33 on 2008-01-03
there is a menu at the top called "thread tools" that has the option available to the thread starter.

---

