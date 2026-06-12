---
title: "internet problems"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by alloftheabove on 2008-01-26
I'm using Ubuntu 7.10, and a router provided by Comcast.  My problem isn't that I can't connect to the internet, it's that it seems as though ONLY firefox is allowed to connect to the internet.  I just got it up today, and Ubuntu recognizes the ethernet connection.  I wanted to install bluefish, so I ran
```
sudo apt-get install bluefish
```
It said that it couldn't find the bluefish package.
I opened Synaptic and searched for libgtk2.0-dev, it didn't find anything.
I opened add/remove programs, and when I try to mark a program for installation,
It tells me that it needs to reload the list.  It always says that.
Here is my ifconfig info:
```
alex@alex-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:39:AF:75  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe39:af75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:1 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43185 (42.1 KB)  TX bytes:5387 (5.2 KB)
          Interrupt:9 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

Anyone got any ideas?

---

### Post by taurus on 2008-01-26
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of all the lines except the last one, Source code and the Cdrom in the bottom window.  Close it and press Refresh.  Now, see if you can find bluefish in the Search field.

---

### Post by alloftheabove on 2008-01-26
thank you so much, it appears to have fixed the problem!

---

