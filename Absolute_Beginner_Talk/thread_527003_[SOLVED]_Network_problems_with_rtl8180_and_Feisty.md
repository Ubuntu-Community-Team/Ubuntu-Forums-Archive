---
title: "[SOLVED] Network problems with rtl8180 and Feisty"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by rubenverweij on 2007-08-16
Hi everyone,

I just installed Feisty and I am new to Ubuntu. When I tried to access the internet, my network manager told me there was no device present. After some searching I installed ndiswrapper with the driver I used in my XP. I tried ndiswrapper -l, and it said the driver was correctly installed. However, when I looked at the graphic tool of ndiswrapper, it said: Device present: no. I could view some acces points, and I configured the AP, key etc. using iwconfig. The problem was: I got no ip address etc. Then I found a topic on the Ubuntu forums about the standard driver r818x. I removed it from the blacklist, and tried modprobe r818x. However, it said that none such module existed. And now I'm stuck. Any help would be greatly appreciated. 

Thanks in advance!

Ruben

---

### Post by rubenverweij on 2007-08-16
Here is some extra info:

> ndiswrapper -l:
---
netr8180 : driver installed
        device (10EC:8180) present
---
ifconfig:
---
wlan0     Link encap:Ethernet  HWaddr 00:50:FC:D0:81:4F            
	  inet6 addr: fe80::250:fcff:fed0:814f/64 Scope:Link          
	  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
	  RX packets:8 errors:0 dropped:0 overruns:0 frame:0          
	  TX packets:7 errors:0 dropped:0 overruns:0 carrier:0          
	  collisions:0 txqueuelen:1000           
	  RX bytes:400 (400.0 b)  TX bytes:558 (558.0 b)          
	  Interrupt:18 Memory:ed800000-ed800025 
---
iwconfig:
---
wlan0     IEEE 802.11b  ESSID:"[essid]"            
	  Mode:Managed  Frequency:2.447 GHz  Access Point:[ap]             
	  Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3            
	  RTS thr=2432 B   Fragment thr=2432 B             
	  Encryption key:[key]   Security mode:open          
	  Power Management:off          
	  Link Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm          
	  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          
	  Tx excessive retries:1  Invalid misc:1619983024   
	  Missed beacon:0
---
dhclient:
---
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/wlan0/00:50:fc:d0:81:4f
Sending on   LPF/wlan0/00:50:fc:d0:81:4f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
---
ndiswrapper -v:
---
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 

---

### Post by rubenverweij on 2007-08-18
Can someone please help me? I tried everything, but nothing works...

---

### Post by rubenverweij on 2007-08-24
I fixed the version problem. I downloaded the latest version of ndiswrapper, it said: device present, and I can see my own network listed when I type iwlist wlan0 scan, but I can't connect to the network....

---

### Post by quinnten83 on 2007-08-24
Sorry dude, 
no idea there, as I ahve been fortunate enough not having to go through this problem.
if you can get a wired connection, try installing wlassistant ( I think, i'm not sure anymore). It sometimes works better than the native network manager of ubuntu, it might do the trick..

---

### Post by rubenverweij on 2008-01-26
Thanks for your help. The problem has been solved by updating to Ubuntu 7.10 and using MAC-filtering instead of WEP-encryption.

---

