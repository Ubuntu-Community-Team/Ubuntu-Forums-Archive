---
title: "configuring the internet in ubuntu with a NIC and a router"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by BBlight on 2007-06-20
Hello,

i installed ubuntu the other day and it does not connect to the internet through my ethernet socket and router..

i have searched this forum and read the advice

i see the main information here...

ifconfig -a
-------------------------------------------------------------------------------------------------

eth0     Link encap: Ethernet  HWaddr 00:40:F4:89:2e:F3
            inet addr:192.168.1.2  Bcast:192.168.1.255 Mask 255.255.255.0
            inet6 addr :Fe80::240:f4ff:fe89:2ef 3/64  Scope:Link
            UP BROADCAST RUNNING MULTICAST   MTU:1500  Metric:1
            RX packets:8 errors:0 dropped:0 overruns:0 frame:0
            TX packets:41 errors 0 dropped 0 overurns:0 carrier 0
            collisions:0 txqueuelen:1000
            RX bytes:1044 (1.0KiB)  TX bytes :6644
            interrupt:11 Base address:0x4000 (6.4KiB)

lo         Link encap: Local Loopback
           inet addr : 127.0.0.1 Mask 255.0.0.0
           inet6 addr ::1/128   scope:Host
           UP LOOPBACK RUNNING MTO :16436  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame=0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier=0
           collisions:0 txqueelen:0 carrier:0
           RX byets:0 (0.0b)  TX byets  (0.0b)

-------------------------------------------------------------------------------------

as far as i know my ips is very standard...PLUSNET.....i think it uses DCHP....

i have a hunch the ubuntu network needs configuring and the router...

my ISP has emailed all the setting values they say any ethernet ROUTER needs...but hey have not included the DNS in this list...

my router has a book with it....and i first tried getting it working under winXP but had ZERO luck on both ethernet or USB.....even after doing the configuring and saving it to flash etc.....the web just would not work....(it installed all the correct USB drivers in winXP..... and still did not work)

this is disconcerting...the fact that the router did not work in winXP with USB drivers installed.......... and the configuration done exactly by the book...

i can post all the settings required for my router....in this forum....

as for ubuntu...i have never touched any settings to do with the internet....apart from the command listed above...

can you help

thanks

Ian

---

### Post by PartisanEntity on 2007-06-20
have you tried typing the following into the terminal:

 ```
sudo dhclient
```

---

### Post by BBlight on 2007-06-20
Hello there

no i have not tried that command...

i will try it...but i think there are several settings that need doing in the ubuntu NETWORK area...

but i will ry it...

the router reports the ethernet and the DSL correctly....you can see it is trying to work...somehow...

my router's IP address is 192.168.1.1
                        Mask  255.255.255.0

and i set all this in configuration...under winXP...into it's flash...

anyhow thanks

V

---

### Post by PartisanEntity on 2007-06-20
It might be worth a try, I have rarely used ethernet, but when I did, I simply plugged the cable in and it would work, when it didn't a *sudo dhclient* would obtain a lease from the router and then it did work.

Let us know if it helped.

---

