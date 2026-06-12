---
title: "unfriendly dell?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by juventus1 on 2007-03-18
hey guys, i have a dell inspiron e1405 and my wireless card is broadcom 4311
my problem is that i can not connect to the internet with my laptop either through wireless or through the wire

everything in my pc works fine when i switch to windows, and my desktop (connected to the same router) works fine. 

I did try the few how to guides for wireless, but i also have the problem that my wired internet doesnt work
i even tried changing my network connection properties (in the top right of the desktop) from "lo" to eth0, ( i dont think i have internet, i think i have lan, but lan0 doesnt do anything)
when i put in eth0 the status changes to disconnected, i then click enable this connection and set it to automatic configuration, but nothing happens,

i've been searching for days to try and find an answer to this problem of the internet on my laptop. (i'm a newbie, if you already havent been able to tell)
thanks for any help!

---

### Post by Hoag on 2007-03-18
I'm afraid I can't offer any help in how to sort it all out, as I was pretty much walked through it some time ago, but I'm using a Dell Inspirion 1300, with a Broadcom card. 

I managed to get both wired and wireless internet working, wireless taking a lot more effort, but stick in there, and you won't regret the effort you put in!

---

### Post by juventus1 on 2007-03-18
haha, thanks! i am deffinately not planning on giving up. I am going to learn all this linux stuff eventually, and for sure i am going to get this to work
hopefully someone can help me out though!

---

### Post by dbott67 on 2007-03-18
I've got a Dell 6400 with Broadcom 8311... this is how I got it working:
[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

-Dave

---

### Post by juventus1 on 2007-03-18
thanks! i'm gonna go try that
but thats just wireless, would youhave any idea why it isnt working even with the wire? i heard that wireless was more difficult to get working!
but thank you very much!!

---

### Post by dbott67 on 2007-03-18
It may be a hardware driver issue.  Can you post the output of th following commands:
```
ifconfig -a
```
Here's mine for comparison:
```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command outputs the network hardware detected:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

-Dave

---

### Post by juventus1 on 2007-03-19
hey dbott
these are the outputs for the commands you asked for.  I cant copy and paste because right now i'm on my desktop, the wired internet for my laptop isnt working either

but for the ifconfig -a the only difference was that that my rx and tx bytes (under lo) was much lower it was at 980

here are the results for the next one(sudo lshw -C network)
these are not copy and pasted btw

network UNCLAIMED
description:Network controller
product: Broadcom Corporation
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0c:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: iomemory:dfdfc000-dfdfffff irq:4
network DISABLED
description:Ethernet interface
product: BCM4401-B0 100Base-TX
vendorBroadcom Corporation
physical id:0 
bus info: pc@02:00.0
logical name: eth0
version: 02
serial: 00:15:c5:6a:dd:69
width: 32 bits
clock: 33 MHz
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=b44 driverversion=1.00 link=no multic
ast=yes
resources: iomemory:df9fe000=df0fffff irq:177



the first looks fairly similar (cept that one part) but the second is noticably different especially the part aboutmy network being disabled and also a bunch of missing info
hope you can give me some help given this information
thanks

---

### Post by juventus1 on 2007-03-21
bump.

---

### Post by dbott67 on 2007-03-23
Sorry for the delay... 

Your wired interface is eth0.  Try activating it using the following command (make sure the ethernet cable is plugged in):
1. Bring down interface:
```
sudo ifdown eth0
```
2. Bring up interface:
```
sudo ifup eth0
```

Check the output of ifconfig again:
```
ifconfig
```

If it shows that eth0 has a valid IP address then it may be a missing entry in your /etc/network/interfaces file.

-Dave

---

