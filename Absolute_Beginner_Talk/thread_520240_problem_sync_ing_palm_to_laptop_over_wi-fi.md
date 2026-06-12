---
title: "problem sync ing palm to laptop over wi-fi"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Elf on horseback on 2007-08-07
so i have spent way too long thinking about this (my brain is mush).  my problem is that i am trying to sync my Palm (TX) up to my laptop via wi-fi.  I desided to go wi-fi becouse i read where the port or some ID type number keeps changing each time you plug your palm back in.  so wi-fi seemed easer.  unless i reboot my laptop, grr, IP address changes.

My list of questions are:

[LIST=1]
[*]Is there a better (easier) way other then wi-fi to sync a palm? (PDA has built in wi-fi)
[*]Is there a way to find out my local IP address and lock it in so when ever i reboot i have the same IP address?
[*]What is my IP address? (ifconfig below)
[*]As it stands right mow now i have Evulation taking care of my sync ing, if my PDA is syncing over wi-fi how do i change it to Jpilot?
[/LIST]



$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:A9:30:CE:4B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:16:6F:95:F9:51  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe95:f951/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4349 errors:4 dropped:4 overruns:0 frame:0
          TX packets:3292 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2925499 (2.7 MiB)  TX bytes:633498 (618.6 KiB)
          Interrupt:22 Base address:0x4000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1704 (1.6 KiB)  TX bytes:1704 (1.6 KiB)


almost for got, I got the sync to work once then i rebooted and it no longer worked

so all in all, I need help please

---

### Post by e_james on 2007-08-09
I'm no expert but I may be able to make some useful comments.

It looks like your IP address is 192.168.1.101. This is a slightly unusual value if it is assigned automatically (DHCP). It would be more common to see something like 192.168.1.3.

For network configuration details the following links should be a good starting point.
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)
[https://help.ubuntu.com/community/PortableDevices](https://help.ubuntu.com/community/PortableDevices)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Ubuntu 7.04 has a Network Manager application. This can sometimes be unhelpful if you want to do something a little bit unusual.

You can set a static IP address if necessary via System | Administration | Networking. (CAUTION - you might disable your internet connection if you get it wrong.) 

If you want some explanation of static and dynamic addressing, these links look useful
[http://en.wikipedia.org/wiki/Internet_protocol_suite](http://en.wikipedia.org/wiki/Internet_protocol_suite)
[http://www.itprc.com/tcpipfaq/](http://www.itprc.com/tcpipfaq/)

If you need any additional explanation, I can try as far as my knowledge will go.

---

