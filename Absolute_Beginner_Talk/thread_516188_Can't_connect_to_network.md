---
title: "Can't connect to network"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by JSFS on 2007-08-02
Hi,
 I'm having great difficulty connecting to my network. A brief history - I originally partitioned my drive, running Windows Vista on one part and Ubuntu ("Feisty Fawn") - that was last week. 

 For the first six days, everything was great - no problems whatsoever. Then yesterday, something went very wrong. After getting back from work last night, I noticed that I could no longer connect to the network on UBUNTU (in particular, ssh and Firefox) -  everything was fine with Vista. Anyway, after having reinstalled UBUNTU two or three times in a desperate attempt to correct the problem, and hours spent searching around the internet, I am now totally confused and stuck.

 Typing "ifconfig" produces the following results:

~$ ifconfig

eth0      
Link encap:Ethernet  HWaddr 00:19:21:A2:4A:30  
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000           
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Interrupt:21 Base address:0xc00 

eth0:avah 
Link encap:Ethernet  HWaddr 00:19:21:A2:4A:30            
inet addr:169.254.4.90  Bcast:169.254.255.255  Mask:255.255.0.          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
Interrupt:21 Base address:0xc00 

lo        
Link encap:Local Loopback            
inet addr:127.0.0.1  Mask:255.0.0.0          
inet6 addr: ::1/128 Scope:Host          
UP LOOPBACK RUNNING  MTU:16436  Metric:1          
RX packets:471 errors:0 dropped:0 overruns:0 frame:0          
TX packets:471 errors:0 dropped:0 overruns:0 carrier:0      
collisions:0 txqueuelen:0           
RX bytes:44880 (43.8 KiB)  TX bytes:44880 (43.8 KiB)

 I've got a very basic idea of what a lot of this means - however, what device does "eth0:avah" refer to, and how does this differ from "eth0"?

 Anyway, any help on getting my connection working again would be very much appreciated!

---

### Post by e_james on 2007-08-03
I probably can't be of much help but I can suggest, for the benefit of someone who is more of an expert than me, that it would be helpful if you could explain what you mean by 'network'. This will determine what diagnostic tests are likely to be useful. For instance, are you connecting to the internet via a router? Is your connection wired or wireless? Are there other PCs or even items like Playstations or VOIP phones?

---

