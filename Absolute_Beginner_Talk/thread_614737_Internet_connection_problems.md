---
title: "Internet connection problems"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Armor Nick on 2007-11-16
Hey everyone,

I have recently installed Ubuntu 6.10 on a virtual machine made with VMWare. I have a speedtouch 530 modem with both an ethernet and a USB router. I have an ADSL connection (Skynet; Belgium). I have already tried to configure it with pppoeconf like the wiki said, but I still can't connect to the internet with it. this is the terminal output:
```
armornick@Ubuntu:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
armornick@Ubuntu:~$ plog
Nov 16 16:29:10 Ubuntu pppd[3350]: Timeout waiting for PADS packets
Nov 16 16:29:10 Ubuntu pppd[3350]: Unable to complete PPPoE Discovery
Nov 16 16:30:00 Ubuntu pppd[5161]: Timeout waiting for PADS packets
Nov 16 16:30:00 Ubuntu pppd[5161]: Unable to complete PPPoE Discovery
Nov 16 16:30:15 Ubuntu pppd[3350]: Timeout waiting for PADS packets
Nov 16 16:30:15 Ubuntu pppd[3350]: Unable to complete PPPoE Discovery
Nov 16 16:30:15 Ubuntu pppd[3350]: Exit.
Nov 16 16:30:34 Ubuntu pppd[5637]: Plugin rp-pppoe.so loaded.
Nov 16 16:30:34 Ubuntu pppd[5639]: pppd 2.4.4 started by root, uid 0
armornick@Ubuntu:~$ plog
Nov 16 16:29:10 Ubuntu pppd[3350]: Timeout waiting for PADS packets
Nov 16 16:29:10 Ubuntu pppd[3350]: Unable to complete PPPoE Discovery
Nov 16 16:30:00 Ubuntu pppd[5161]: Timeout waiting for PADS packets
Nov 16 16:30:00 Ubuntu pppd[5161]: Unable to complete PPPoE Discovery
Nov 16 16:30:15 Ubuntu pppd[3350]: Timeout waiting for PADS packets
Nov 16 16:30:15 Ubuntu pppd[3350]: Unable to complete PPPoE Discovery
Nov 16 16:30:15 Ubuntu pppd[3350]: Exit.
Nov 16 16:30:34 Ubuntu pppd[5637]: Plugin rp-pppoe.so loaded.
Nov 16 16:30:34 Ubuntu pppd[5639]: pppd 2.4.4 started by root, uid 0
armornick@Ubuntu:~$ pon dsl-provider
Plugin rp-pppoe.so loaded.
armornick@Ubuntu:~$ plog
Nov 16 16:30:00 Ubuntu pppd[5161]: Unable to complete PPPoE Discovery
Nov 16 16:30:15 Ubuntu pppd[3350]: Timeout waiting for PADS packets
Nov 16 16:30:15 Ubuntu pppd[3350]: Unable to complete PPPoE Discovery
Nov 16 16:30:15 Ubuntu pppd[3350]: Exit.
Nov 16 16:30:34 Ubuntu pppd[5637]: Plugin rp-pppoe.so loaded.
Nov 16 16:30:34 Ubuntu pppd[5639]: pppd 2.4.4 started by root, uid 0
Nov 16 16:31:05 Ubuntu pppd[5161]: Timeout waiting for PADS packets
Nov 16 16:31:05 Ubuntu pppd[5161]: Unable to complete PPPoE Discovery
Nov 16 16:31:07 Ubuntu pppd[5668]: Plugin rp-pppoe.so loaded.
Nov 16 16:31:07 Ubuntu pppd[5670]: pppd 2.4.4 started by armornick, uid 1000
armornick@Ubuntu:~$ 

```

---

### Post by paradoxni on 2007-11-16
The way I understand it is you should connect to the internet using the Host operating system, then simple configure your VMware to use NAT and the internet should just work. I dont think you need to configure your adsl within ubuntu vmware session.

---

### Post by Armor Nick on 2007-11-16
Yes, I tried this but it didn't work. I already tried 'Bridged', 'NAT' and 'Host-only', but none of them work. Firefox still claims not being able to find the server.

On a side-note, I tried this with a live-cd too and it didn't work either.

---

### Post by zvacet on 2007-11-16
system>administration<network<select your modem<properties>select type of connection(dhcp,static)>close>in DNS tab you will find address and it is from your router>add your dns>close>general tab<tick your modem and box with **changinig network interfaces ** will show.After this is finished close.

```
pppoeconf
```

---

### Post by paradoxni on 2007-11-16
so you have connected the internet in host OS? and verified the internet is working there first, then set Vbox to use NAT?

If your host is XP, is vbox added to your built in firewall to allow connection?

---

