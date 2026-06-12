---
title: "[SOLVED] Newbie to LAN connections needs help."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by TheThinker on 2007-06-14
Thanks for everyone's help! I have a Celeron D processor (2.8 GHZ) with Ubuntu Feisty and for some reason I can't get my LAN connection to work. I'm attempting to connect with my brother's Window-XP computer through LAN but no matter what I do it seems as if his computer gets no packets back. I don't know where the problem is!

Both of our subnet-masks are 255.255.255.0 and my IP Address for ETH1 (I know it works through the Network Tools) is 162.128.1.2. My brother's IP address is 162.128.1.1. This should work, yet it doesn't. Any help would be greatly appreciated once again!

---

### Post by lazyart on 2007-06-14
How are these machines connected to each other?

---

### Post by shearn89 on 2007-06-14
have you tried using samba? Terminal version is:
```

smbclient <path to shared folder> -U <username>

```

else just create a launcher with the URL smb://<yoursharehere>
and click on it. 
However if you're not trying to share docs, this is all useless....

---

### Post by lazyart on 2007-06-14
We have to get connectivity established before we start talking Samba....

---

### Post by nymphaeles on 2007-06-14
do an ifconfig from the Linux machine and verify your IP/submask
do an ipconfig /all from the XP machine and verify its IP/submask

ping the XP machine from the Linux machine and see if you have any replies?
ping the Linux machine from the XP machine and see if you have any replies?
do a tracert Linux-IP from the XP to see where the packets stop.

Post your results here for more help

---

### Post by TheThinker on 2007-06-14
nymphaeles:

Eek! I'm at college at the moment, so I'll post the results of the trace-root later today (although I have used it before and it seemed fine to me, but I'm a noob). I have, however, pinged my brother's XP machine and got replies. But the speed listed on my machine during the ping was something like 0.28 kb/sec. My brother's machine read something way above that; I'll post that stuff later. Unfortunately, I don't know how to ping my machine through my brother's XP machine. Does Windows XP come with ping tool? How do I activate it? I looked for it on his com with no success.

Oh, and thanks for that terminal tip to verify the IP addresses. I'll try it on Linux, but I don't know how to try it on XP. Help?

lazyart:

Both machines are directly-connected via their ethernet ports (no PCI cards or anything like that). Thus there is no gateway or anything like that. This network is strickly just 2 computers. Before with XP I was able to get them to connect by simply giving them both the same subnet masks and slightly different IP addresses on their connections, but even then it was problematic. I don't know why, but I always have problems with LAN connections, at least when there are only two computers on a network.

shearn89:

No, I'm not planning to share docs with my brother's machine, although that may come useful in the future. This connection is meant for us to play some multiplayer games, specifically Open Arena. We both have the same version# of the game, just differen O.S. versions of course. So far the game shows no listing of "servers" (which I find to be very confusing since it isn't clear whether it can only connect to dedicated servers on a LAN).

---

### Post by nymphaeles on 2007-06-14
In the XP machine, go to Start, Run, type in cmd to open a command promt.  In the cmd window, type ping IP, type tracert IP, etc.
By the way, in the Ubuntu machine, go to system, network tools, they have a set of tools including ping, tracert, .. nicely orginized in tabs.

tracert stands for trace route, which is the path through which the packets travel...

---

### Post by TheThinker on 2007-06-14
Thanks. I'll try it as soon as I get home. Expect my results by tonight.

---

### Post by lazyart on 2007-06-14
> **TheThinker said:**
> 
lazyart:

Both machines are directly-connected via their ethernet ports (no PCI cards or anything like that). Thus there is no gateway or anything like that. This network is strickly just 2 computers. Before with XP I was able to get them to connect by simply giving them both the same subnet masks and slightly different IP addresses on their connections, but even then it was problematic. I don't know why, but I always have problems with LAN connections, at least when there are only two computers on a network.


This is what I suspected.  Are you using a crossover cable?  If not this isn't going to work.
Either that or a hub to connect the machines.

---

### Post by nymphaeles on 2007-06-14
lazyart already answered your question.  I didn't read that part closely.
Sure, you need a hub, a switch, or a cross-over cable for the direct connection as you described.  However, those troubleshooting tools should give you an idea that a connection can or can't be established in between the 2 machines.

---

### Post by TheThinker on 2007-06-14
Here are the results of all those tests nymphaeles suggested. I seperated each test using -----. Keep in mind that my Ubuntu computer uses the IP address 162.128.1.2. My brother's is 162.128.1.1. 
-------------------------------------------------------------------------
--------------------------------------------------------------------------
Traceroute results from my Feisty computer by typing 162.128.1.1  :

HOP|       Hostname      |    IP             | Time1
   1   162.128.1.2           162.128.1.2          0.23ms   
   1   162.128.1.2           162.128.1.2       3001.229ms
-----------------------------------------------------------------------
Traceroute results from brother's XP machine by typing 162.128.1.2  :

Tracing route from 162.128.1.2 over a maximum of 30 hops
   1 Destination host unreachable.
------------------------------------------------------------------------
Ping request from my Linux machine to 162.128.1.1: Failed (zip, zero, nada)
----------------------------------------------------------------------------
Ping request from XP machine to 162.128.1.2 says this:

Pinging 162.128.1.2 with 32 bytes of data:
Destination host unreachable
Destination host unreachable
Destination host unreachable
Destination host unreachable
Ping statistics for 162.128.1.2:
Packets Sent=4 Packets Received=0 Packets Lost=4 (100% loss)
-------------------------------------------------------------
Results from the ifconfig on my Ubuntu Feisty Computer:

eth0      Link encap:Ethernet  HWaddr 00:05:5D:34:B7:D4  
          inet addr:128.162.1.2  Bcast:128.162.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x6c00 

eth1      Link encap:Ethernet  HWaddr 00:11:11:A7:31:4F  
          inet addr:162.128.1.2  Bcast:162.128.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fea7:314f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3410 (3.3 KiB)  TX bytes:378 (378.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72780 (71.0 KiB)  TX bytes:72780 (71.0 KiB)
-----------------------------------------------------------------------
Results from the XP ipconfig /all command from my brother's computer:

Windows XP IP configuration (yup that's the only thing it says. I typed everything correctly it seems)
----------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------

Well there you go. nymphaeles, I don't know whether I have a cross-over cable connected; it's a yellow ethernet cable, and it's been successful in the past in connecting both our computers through LAN when they were both Windows-XP based. It was mostly succesful with IPX protocol-games and the like, so the TCP/IP thing was sporadically good at times. That's all I know. Do I really need a hub or a switch for a two-computer network? Seems rather odd in my opinion.

I'll come back again tomorrow guys. Let me know if you find anything wrong with these results. Yeah, I know, the XP ipconfig /all really didn't give me anything to tell you that was useful. This leads me to suspect that the problem resides in the XP computer, but that's just my guess.

---

### Post by nymphaeles on 2007-06-14
Best to get a switch.  You may find it's hard to look for a cross-over cable.
I also note that you have static IPs configured on both machines.  Why do you have eth0 & eth1 both have the same IP?  Even if you have 2 NICs in the same machine, they must have different IPs.
You may want to get a switch, reconfigure both machines to use DHCP, and everything should be fine.

---

### Post by lazyart on 2007-06-14
You don't NEED a hub or a switch if you have a crossover cable.  You can look at the ends of the yellow cable to see if it is a crossover-- If all the colors line up when they face the same direction then it's a straight patch.  If two of the colors don't line up then it's a crossover.

Looks like the problem is with the XP machine because you have no output of ipconfig.  You could check device manager to see if there is a red x or yellow question mark.  Maybe even uninstall it from device manager and rebooting.

Looking at the ifconfig output you have two NICs in your ubuntu machine-- eth0 and eth1?  I would disable one of them.  With them both having the same IP it could get confusing (those I see traffic is only trying to flow from eth1).

---

### Post by TheThinker on 2007-06-15
Thanks guys! Yeah, I'll change Eth0 to different IP address. That may clear things up. Later on today I'll look at my cable to check it if it's a cross-over and check the device-manager on the XP to see if anything's wrong. I'll be back with those results at around after I get out of college. Again, thanks for your help! ;)

---

### Post by TheThinker on 2007-06-15
Better yet, I'll just disable Eth0 altogether. What's a little annoying is that whenever I change a certain setting in the Network window, such as an IP address, both of my Ethernet devices are switched on and my modem switched off. Shouldn't be much of a problem though if I simply just uncheck Eth0. In case you're wondering, Eth0 is my D-link PCI card left over from when I had XP. I probably should remove it.

---

### Post by TheThinker on 2007-06-21
(sigh) It's been a while since I last posted. College has been hell. Here's the scoop:

Hmmm. I'm confused about the cable, Lazyart. Are the colors on it supposed to be grouped together in sections for a straight patch and is the crossover supposed to have two colors not grouped together? I got confused about your directions. If I understand you correctly, it looks like a straight patch. Oh well.

From what I gather from all of this it seems as if I'm really close to fixing the connection. I'll buy a crossover cable and see if I can re-install my brother's drivers. That may fix the problem.

---

### Post by TheThinker on 2007-09-14
I know this is already an old thread, but thanks for the help! It turned out that it was my brother's XP machine. His network settings involved some sort of Nvidia network driver. Strange. We switched it off and voila! We pinged each other and began playing. The only drawback was that only I could host a game on my computer, not him. Oh well. Problem Solved.

---

