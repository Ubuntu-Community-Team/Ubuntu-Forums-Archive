---
title: "My System is Running REALLY Slow"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by btwong on 2007-12-09
OK, i have just installed Ubuntu GUtsy Gibbon, and everything was running really smoothly and fast, but then seemed to slow right down.

I think it was when i changed some Network settings.

Right now, when i first turn on my puter, ubuntu takes ages to load. It even goes from the splash screen and shows all the drivers loading. Then once i get to the login screen and login, it takes about 1 minute for everything to load so that i can use it. When i load any program once using Ubuntu (firefox, thunderbird, rhythmbox, even any hard drives or folders) it takes about 10 seconds to do so.

After reading up, i have read some where that it might be my network settings. I can still use the internet fine, but this is frustrating the hell out of me.

I found this thread ([http://ubuntuforums.org/showthread.php?t=317489]("http://ubuntuforums.org/showthread.php?t=317489") and i have decided to post the same commands:

cat /etc/resolv.conf
> nameserver 192.168.1.101

route -n
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.101   0.0.0.0         UG    100    0        0 eth0


ifconfig -a
> eth0      Link encap:Ethernet  HWaddr 00:15:C5:7A:F1:15  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe7a:f115/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61072837 (58.2 MB)  TX bytes:2683026 (2.5 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16396 (16.0 KB)  TX bytes:16396 (16.0 KB)


My adsl modem's ip address is 192.168.1.101.

Can anyone help me? or tell me if i am even on the right track?

thanks

---

### Post by LostMagix on 2007-12-09
what are your system specs

---

### Post by btwong on 2007-12-09
its a laptop.
Dell inspiron 640m
2 gig ram
core duo2 t5300 cpu
4 gig swap space. 40 gig for the system files.

i bought the system about 6 months ago.

---

### Post by btwong on 2007-12-09
bump...


i need help!!

---

