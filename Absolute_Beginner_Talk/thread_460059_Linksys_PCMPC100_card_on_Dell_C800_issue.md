---
title: "Linksys PCMPC100 card on Dell C800 issue"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by rookie48 on 2007-05-31
I'm running Ubuntu 7.04 on a Dell C800. The installation has gone well, but I cannot get the Linksys PCMPC100 PCMCIA card to work on my DHCP network.  The network icon suggests it is connected to the wired network, but no connection exists. My router logs suggest the following: 

May 31 08:23:40 (none) user.warn klogd: unregister mac on radio 0 00:06:25:29:0C:30 
May 31 08:23:40 (none) user.debug klogd: wns msg rcvd: type = 0x130a^Ilength = 30 
May 31 08:23:40 (none) user.warn klogd: register link id 1 mac on radio 0 00:06:25:29:0C:30 
May 31 08:23:40 (none) user.err AA: aniAsfTimer.c:445 Null Duration  
May 31 08:23:40 (none) user.debug klogd: wns msg rcvd: type = 0x1308^Ilength = 46 


The network device speed is listed as "unknown" in Ubuntu. 

I could really use some help in diagnosing this problem and trying to get it fixed.... not "learned" in the ways of Ubuntu yet...

Help!

---

### Post by kernel tom on 2007-05-31
so i'm assuming this is a wireless network you are trying to connect to

go to Network Settings in Ubuntu and make sure that ur device is enabled, to do so you may need to know the exacy name of your network

---

### Post by rookie48 on 2007-06-04
This is a "wired" device. It is enabled.....

---

### Post by rookie48 on 2007-06-06
Has anyone gotten a Linksys PCMPC100 EtherFast PCMCIA card to work properly in Ubuntu 7.04? If so, can you provide the card properties from the Network tools? The card is connecting, but not registering an IP address from the DHCP server (Linksys router).

---

