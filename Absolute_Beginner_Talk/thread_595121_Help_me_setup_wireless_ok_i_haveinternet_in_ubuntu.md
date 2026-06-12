---
title: "Help me setup wireless ok i haveinternet in ubuntu fiesty fawn"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-10-28
i use a wireless card to connect to my router, the card is D-Link AirPlus G DWL-G630

ubuntu has recognized this and it appears to be properly working.

i cant connect to the internet. i bilieve it has to do something with the settings.

im attaching a screenshot of my settings in winxp, where shud i enter these settings in ubuntu.

so far i used automatic configuration and entered the DNS and alternate DNS in the DNS tab of ubuntu.

---

### Post by faraz_k86 on 2007-10-28
I have also run ifconfig on the system and im adding the result below:

```
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:F3:86:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4612 (4.5 KiB)  TX bytes:4612 (4.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:19:5B:79:9B:49  
          inet6 addr: fe80::219:5bff:fe79:9b49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:1 dropped:1 overruns:0 carrier:0
          collisions:4 txqueuelen:1000 
          RX bytes:409637 (400.0 KiB)  TX bytes:2848 (2.7 KiB)
          Interrupt:16
```

---

### Post by llamakc on 2007-10-28
What happens if you type in the Terminal:

```

sudo dhclient ra0

```

Look at the output of ifconfig again and see if ra0 gets an IP.

---

### Post by faraz_k86 on 2007-10-28
the command sudo dhclient ra0 did it my internet is working now. here are the results of that command 

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:19:5b:79:9b:49
Sending on   LPF/ra0/00:19:5b:79:9b:49
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 953836268 seconds.


```

can any1 please explain to me what that command does and how it worked, i did not even enter my dns numbers in th properties so how is it working???

---

### Post by faraz_k86 on 2007-12-19
i know im digging up a very old post, but i still did not get a reply to my previous question.

can anyone please answer that

---

### Post by walkerk on 2007-12-19
> **faraz_k86 said:**
> i know im digging up a very old post, but i still did not get a reply to my previous question.

can anyone please answer that

Your wireless router has DCHP enabled. If you use dhclient it requests an IP, Subnet Mask, and DNS settings... all of which it will provide.

Your router gets its settings from your ISP as your router is using DHCP to get the same info from the ISP.

Your router will offer you a Local Area Network IP and settings. You're actually using the ISPs DNS servers to resolve.

Does this answer your question?

---

### Post by faraz_k86 on 2007-12-19
yes it does thanks a lot

so the command for that is sudo dhclient ra0

ok thats another one to remember.......sigh :(



also what does ipconfig do?

the result that i poted above is of ipconfig


what is eth0, lo and ra0  all of which are in the ipconfig result

---

### Post by walkerk on 2007-12-19
> **faraz_k86 said:**
> yes it does thanks a lot

so the command for that is sudo dhclient ra0

ok thats another one to remember.......sigh :(



also what does ipconfig do?

the result that i poted above is of ipconfig


what is eth0, lo and ra0  all of which are in the ipconfig result

**ifconfig** shows your network interface configurations. (to manually edit them type **gksu gedit /etc/network/interfaces**)

lo = loopback
eth0 = your wired interface
ra0 = your wireless interface


if you use [wicd]("http://wicd.sourceforge.net") you can edit the preferences and set your wireless interface to [ ra0 ] .. i highly suggest it over network-manager. give it a try...

---

