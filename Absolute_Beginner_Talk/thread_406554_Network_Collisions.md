---
title: "Network Collisions"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by wesw02 on 2007-04-11
Hey guys,
     Today was my first time working with ubuntu, and I like it so far. I'm having a small problem though, I am receiving alot of network collisions when transferring stuff from a windows XP laptop to my ubuntu machine via smb. The network collision light on my switch is going nuts, speed is around 600KB/s (it should be much higher), and notice below my ifconfig results show 'collisions:3520757'. Can some give me an idea what could be causing this problem.


eth0      
          Link encap:Ethernet  HWaddr 00:50:04:67:F2:4C
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fe67:f24c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21477502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12538632 errors:0 dropped:0 overruns:0 carrier:2
          collisions:3520757 txqueuelen:1000
          RX bytes:602920240 (574.9 MiB)  TX bytes:950229393 (906.2 MiB)
          Interrupt:193 Base address:0x2000

---

### Post by MikeEvans on 2007-04-11
Some causes of high collision rates are:

[LIST]
[*]To many devices.  Are there other devices on the network besides the two mentioned?
[*]faulty/failing hub/switch.  What type of switch do you have?
[*]Mixed duplex settings.  Make sure all your devices are using full duplex mode.  If that fails you could try everything in half duplex.  If half duplex works it could mean something is wrong with the switch or cabling.
[/LIST]

Although I've never had a collision problem that involved a Linux machine, the issue has usually been related to the hub/switch.  One thing I would recommend doing if you haven't already is power down all network devices, then bring the switch up first, then any routers, then the computers.

---

### Post by Ocelaris on 2007-04-11
I'm having a similar problem on my Edgy Eft box, but I actually am having dropped packets, I do have a mac, PC (XP) and assorted Laptops connected... It's a  Gigabit switch, and fairly new, I'm wondering if it's my network... literally the network manager shows it being disconnected, and being reconnected immediately... but takes a good 6 seconds.

I run citrix, and that seems to be fairly taxing on the network, so wondering if that could be the cause...  but nothing on the citrix site about dropped packets... 

eth1      Link encap:Ethernet  HWaddr 00:16:41:2C:53:08  
          inet addr:172.17.80.115  Bcast:172.17.80.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fe2c:5308/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203424 errors:0 dropped:190 overruns:0 frame:0
          TX packets:185496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62823026 (59.9 MiB)  TX bytes:15460228 (14.7 MiB)
          Base address:0x4000 Memory:da080000-da0a0000

---

### Post by wesw02 on 2007-04-11
> **MikeEvans said:**
> Some causes of high collision rates are:

[LIST]
[*]To many devices.  Are there other devices on the network besides the two mentioned?
[*]faulty/failing hub/switch.  What type of switch do you have?
[*]Mixed duplex settings.  Make sure all your devices are using full duplex mode.  If that fails you could try everything in half duplex.  If half duplex works it could mean something is wrong with the switch or cabling.
[/LIST]

Although I've never had a collision problem that involved a Linux machine, the issue has usually been related to the hub/switch.  One thing I would recommend doing if you haven't already is power down all network devices, then bring the switch up first, then any routers, then the computers.

I was able to track the problem down a little more, it appears that Ubuntu had the network card set to 10BaseT. I tried to change it, however for some reason it was under the impression that this card only supported 10BaseT. At this point I assumed it was a kernel module issue. I pulled that nic out and put another in and it worked like a charm. Thanks for the help ;)

---

### Post by MikeEvans on 2007-04-12
No problem.  Could you provide some identifying information for the two cards for others that might run into the same issue.  

Ocelaris,  A 1gig switch should be able to handle a few devices without any problem.  A few things to start out with:
[LIST]
[*]Just to clarify, is your network running very slow like wesw02's?  If so whats your transfer rate on large files?
[*]Are you seeing dropped packets on your other devices?  
[*]If you ping your gateway do you get dropped packets reported?
[*]Has this same hardware worked before without this issue, maybe with windows installed?
[/LIST]

I think thats a good preliminary check to start narrowing down your issue.  You may want to try the above steps when your network is crowded and when its just your Edgy box.  Also when citrix is running and when its not.  Dropped packets can be caused by a very specific type of packet.

---

