---
title: "problems with internet connection"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by zhongdi on 2007-07-06
I have a problem with the internet connection.I have Ubuntu 6.64 version in my laptop and untill yesterday the cable connection of internet runs without any problem. Yesterday night, I tried to install wifi-radar without success, in order to activate my wireless, today when I  started my computer again and I have activated the eth0 port using the network tool (I have activated it) but no connection of internet is done (however when I plug the internet cable, the led is on). Can everyone helps me? Thank you.

---

### Post by twiceasworn on 2007-07-06
Could you open up a command line and post what comes out of the command "ifconfig"?

---

### Post by zhongdi on 2007-07-06
$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:20:DB:AA
          inet addr:*** Bcast:***  Mask:255.255.192.0
          inet6 addr: fe80::216:36ff:fe20:dbaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:401091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24613665 (23.4 MiB)  TX bytes:4912 (4.7 KiB)
          Interrupt:169 Base address:0x1800

---

