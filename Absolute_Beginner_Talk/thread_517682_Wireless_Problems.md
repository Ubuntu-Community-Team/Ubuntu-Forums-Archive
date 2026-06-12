---
title: "Wireless Problems"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by KillerSiafu on 2007-08-04
I'm running 7.04 on a dell 1420 N laptop, 2.0 Ghz Duo Intel t7300 chip, 2 gb's of ram, SATA 160gb 7200 RPM harddrive,

I have a home wireless network on a linksys router that is just using MAC address filtering for security. I'm having problems consistently connecting. Sometimes it connects fine, and sometimes it won't connect at all. The wireless card's MAC address has been added to the approve list on the router (obviously). I also added the wired network card's MAC address just for a sanity check.

When I try and connect, I'll click on the wireless icon on the top of the screen and select the appropriate wireless network. Sometimes, it connects within 5-10 seconds, othertimes, it will try and connect for a minute or two, then stop trying. I'll attempt to connect again, and still no luck. It went for a 2 day stretch without being able to connect. My other laptop (running XP) can consistently connect with no problems, as can my TiVO and 360 so I'm pretty sure the network is running fine.

My ifconfig looks like:

[INDENT]eth0      Link encap:Ethernet  HWaddr 00:1A:A0:FB:F3:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:7A:DD:17  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe7a:dd17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8519 errors:0 dropped:4048 overruns:0 frame:0
          TX packets:9143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7604860 (7.2 MB)  TX bytes:1671718 (1.5 MB)
          Interrupt:17 Base address:0xa000 Memory:fe8ff000-fe8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:A0:FB:F3:86  
          inet addr:169.254.10.182  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12777 (12.4 KB)  TX bytes:12777 (12.4 KB)
[/INDENT]

My iftab looks like:

[INDENT]# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

# eth0 mac 00:16:76:a5:b8:9f arp 1
[/INDENT]


Any suggestions?

---

### Post by zabien1970 on 2007-08-04
I was having problems and someone suggested switching channels
[http://ubuntuforums.org/showthread.php?t=512404](http://ubuntuforums.org/showthread.php?t=512404)

---

### Post by KillerSiafu on 2007-08-04
I'll look into that... but I get a really strong signal (almost 100%) and like I said, my other computer has no problem connecting at any time. When i can connect (like right now), my connection is great. It seems like it's all or nothing. One thing I noticed when I can't connect, when i refresh my router's MAC address list, it SOMETIMES helps me connect. but again, not always. Obviously what I'm shooting for here is consistency.

---

### Post by MattBD on 2007-08-05
I've had a similar problem since I started using Kubuntu Feisty on my Dell Inspiron 1150 in April. I have another laptop running Windows Vista (yes, it does really suck!) and that has no problem connecting, nor does my PDA or my Sony PSP.
When I try to connect using my Belkin F5D7010uk (Version 6) wireless card, it will start to connect, then it will hang at about 28%. If I keep trying it does  eventually connect (usually).
There is a trick I found that seems to get it working more often. If I try to connect to another network that I don't have the password for (such as a neighbour's), then click on Cancel when the password input screen comes up, then it automatically tries to connect to my network again. For some reason, it seems to be more likely to connect when I do this.
This is a pain, but it hasn't put me off Linux because in Windows XP with the same wireless card my connection was incredibly unreliable (I'd click on a link, then the connection would drop out and I'd have to reconnect).
I've tried the third Alpha of Gutsy, and so far I've connected every time in that, without the need for any tricks of this kind, so you might find that if you change to Gutsy when that is released, that will resolve the issue. But other than the above, I can't suggest a fix for Feisty. If someone CAN provide a solution for this, I'd be very interested to read it.

---

### Post by KillerSiafu on 2007-08-05
Trying what Matt said... That seems to work occasionally... but again not every time. I can usually get the connection working by some combination of restarting the router, re-saving the approved list of mac addresses, disabling / reenabling wireless on the laptop, or trying to connect to a different network and then cancelling.... Sometimes I can connect to the wireless network in 10 seconds, sometimes it takes 10 minutes, and sometimes i cant connect at all.

Extremely annoying...

---

