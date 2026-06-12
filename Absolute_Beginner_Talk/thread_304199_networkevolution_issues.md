---
title: "network/evolution issues"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by yanqui on 2006-11-21
I have successfully installed Ubuntu.  The first day, everything worked.  NOw it looks like none of the settings were sticky.  I can't send/receive email, I can't connect to the internet.  When I read up on these questions, someone always asks, "are you behind a firewall or a router?"  Okay, if I am, how should I go about getting out?  What informaiton do I need to get to configure my system to access the internet?

---

### Post by civetta on 2006-11-21
How are you connecting?

What do you get if you type "ifconfig" into the terminal?

---

### Post by yanqui on 2006-11-21
I have an ethernet card and the connection is active and working.  I did a repair from the cd, and then when i opened evolution, I got a send/receive just fine.  this time it's not wroking.  and firefox opens but won't connect.  output from ifconfig:

link encap: Ethernet  hwaddr 00:a0:d1:36:ab:2a
inet addr 192.168.5.114 bcast 192.168.5.255 mask 255.255.255.0
upbroadcast runnign multicast mtu 1500 metric 1
rx packets 1765 errors 0 dropped 0 overruns 0 frame 0
tx packets 274 errors 0 dropped 0 overruns 0 carrier 0
collisions 0 txqueuelen 1000
rx bytes 660526 (645.0 KiB) tx bytes 19500
interrupt 217 base address 0x8000

there's also information about the wireless and local.

---

