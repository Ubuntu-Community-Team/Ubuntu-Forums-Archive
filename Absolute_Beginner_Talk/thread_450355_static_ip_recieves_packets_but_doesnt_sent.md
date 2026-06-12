---
title: "static ip recieves packets but doesnt sent"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by themish on 2007-05-21
Hello,
I am trying to set my alienware laptop to have a static ip address.  I am very new to linux in general so please bear with me if I need detailed instructions.  I was given the static IP, subnet mask, and default gateway address for the ethernet jack.  I ran the cable to my xp laptop, booted, plugged in the numbers and it worked fine.  I then unplugged the cable, plugged it into the Edgy laptop, used the gui for network 
(system-administration-networking)
Clicked on eth0, the wired connection, changed configuration to static IP address, plugged in the numbers, but no good.  I see a ridiculous amount (several megabytes) of recieved bytes and packets (left it on over 3 nights), but transmitted packets is only 28 with no "transmission errors".  
I figure, since the static ip address, subnet mask, and gateway worked on my XP laptop, that the numbers are good, and that there is some hardware or hardware configuration problem with the laptop.  Any help is appreciated, thanks for your time!

---

### Post by wieman01 on 2007-05-21
What does...
> route
...and...
> ifconfig
...say?

---

### Post by themish on 2007-05-21
> themish@themish-laptop:~$ ping -c l 216.239.51.99
ping: bad number of packets to transmit.
themish@themish-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.220.85.0    *               255.255.255.0   U     0      0        0 eth0
default         128.220.85.1    0.0.0.0         UG    0      0        0 eth0
themish@themish-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0D:02:2A:FA  
          inet addr:128.220.85.65  Bcast:128.220.85.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe02:2afa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1507815 (1.4 MiB)  TX bytes:2088 (2.0 KiB)
          Interrupt:217 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40168 (39.2 KiB)  TX bytes:40168 (39.2 KiB)


Thank you for your time

---

