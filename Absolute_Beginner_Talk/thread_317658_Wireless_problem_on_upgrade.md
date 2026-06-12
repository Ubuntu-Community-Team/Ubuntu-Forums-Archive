---
title: "Wireless problem on upgrade"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by AKASchwanksta on 2006-12-12
Hey.

I just did a fresh install on my laptop of Edgy Eft. Before installing Edgy, I had an install of Dapper. In Dapper I was blown away by the fact that all the wireless problems I had been having in windows were completely gone. The OS immediately recognized my wireless card and it was immediately ready to connect to my network. After installing Edgy, my wireless doesn't work anymore. I think they simplified the network settings portion of the distro. but it has had a negative effect on my system. I really don't want to go back to Dapper but I really need wireless. It says that i have a wireless connection in the network settings however, when I click the essid menu, nothing is displayed. When I type the network that I want to connect to it doesn't work either. 

Is there anything I should try to get this working?

---

### Post by Zelut on 2006-12-12
what wireless card are you using? what is the output of **ifconfig**? ...maybe with some more info we can figure it out.

---

### Post by AKASchwanksta on 2006-12-12
I am using a Intel(R) PRO/Wireless 2200BG Network Connection. My ifconfig looks like this:

eth0      Link encap:Ethernet  HWaddr 00:12:3F:F0:8D:1C  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fef0:8d1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:27054 errors:4244 dropped:0 overruns:0 frame:1259
          TX packets:16841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37351008 (35.6 MiB)  TX bytes:1719701 (1.6 MiB)
          Interrupt:169 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:26:12:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x6000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27716 (27.0 KiB)  TX bytes:27716 (27.0 KiB)

---

### Post by LDRoamer on 2006-12-12
Do you have network manager installed?  I had problems with both my wired and wireless connections.  I could get both working manually from a terminal but I had to get network manager to do it automatically for me. Neither of my wired or wireless connections would work if I tried to configure them through  system -> administraation -> networking.  Now I only have a few weeks linux experience under my belt so this may be of no value.  My suggestion is that if  you aren't using Network Manager you might try that.

---

### Post by AKASchwanksta on 2006-12-12
I just figured it out. It was actually a router problem but what the hell.

---

### Post by Zelut on 2006-12-12
its always something :)

Glad you got it working again.

---

### Post by sailor2001 on 2006-12-12
kwifi and/or wifi-radar are good managers . I prefer kwifi and put it on the panel so I can watch it

---

