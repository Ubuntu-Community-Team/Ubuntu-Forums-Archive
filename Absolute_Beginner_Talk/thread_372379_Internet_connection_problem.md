---
title: "Internet connection problem"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by jgarofalo on 2007-02-28
After installing Dapper Drake, my broadband internet connection works for about 30 seconds, then every website I try to visit times out (using firefox, gaim, and attempting to download software through easy ubuntu).  I noticed that whenever I access network tools through the GUI that lo is always selected as opposed to eth0.  I use a comcast cable modem.  I have tried rebooting the modem and computer and have blacklisted ipv6, neither of which changed the problem.

I've been looking through the forums for a while and nothing seems to work.  I'm not sure which information one would require to figure out what's going on, but if you tell me the command to run, I can put it up.  Thanks for your patience and help while I learn to use linux.

---

### Post by ajmorris on 2007-02-28
> **jgarofalo said:**
> After installing Dapper Drake, my broadband internet connection works for about 30 seconds, then every website I try to visit times out (using firefox, gaim, and attempting to download software through easy ubuntu).  I noticed that whenever I access network tools through the GUI that lo is always selected as opposed to eth0.  I use a comcast cable modem.  I have tried rebooting the modem and computer and have blacklisted ipv6, neither of which changed the problem.

I've been looking through the forums for a while and nothing seems to work.  I'm not sure which information one would require to figure out what's going on, but if you tell me the command to run, I can put it up.  Thanks for your patience and help while I learn to use linux.


What happens when you change it to eth0? Also what happens when you type sudo dhclient in a shell?

---

### Post by jgarofalo on 2007-02-28
When I change the connection device to eth0 and hit OK, it immediately reverts back to lo.

Under network settings > search domains it reads hsd1.pa.comcast.net and shows 2 DNS servers.

The output from sudo dhclient is:

PING 24.0.248.1 (24.0.248.1) 56(84) bytes of data.
--- 24.0.248.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

I also got the output from ifconfig if that's any help

eth0      Link encap:Ethernet  HWaddr 00:08:A1:14:11:0E
          UP BROADCAST MULTICAST  MTU:1500  Metric:1   
          RX packets:11969 errors:238 dropped:0 overruns:0 frame:0 
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0     
          collisions:0 txqueuelen:1000     
          RX bytes:738404 (721.0 KiB)  TX bytes:5030 (4.9 KiB)   
          Interrupt:201 Base address:0xd800 

lo        Link encap:Local Loopback    
          inet addr:127.0.0.1  Mask:255.0.0.0     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1     
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0       
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0     
          collisions:0 txqueuelen:0     
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)


Thank you!

---

