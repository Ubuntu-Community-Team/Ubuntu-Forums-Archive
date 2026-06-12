---
title: "Internet cable broadbend connection"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by James Lee on 2007-06-24
I have installed Ubuntu using Wubi and it seems to be satisfactorily installed except for the internet connection. I did get a warning during the installation that there wsa an error in the network configuration but also got a message saying I could retry from the main menu. This I have been trying to do without success. I've taken the Static IP address configuration and entered the IP address. I have also tried to insert the S/net address and the G/way address but nothing seems to wake up the connection to the Internet.

It all works very well with XP but that only raises the frustration level. Is any one able to help? Will be very grateful for any assistance.

James Lee

---

### Post by mattg89 on 2007-06-24
This is wired, right? Post the contents of
```
sudo ifconfig
```
That might help work out what's wrong.

---

### Post by James Lee on 2007-06-26
Apologies for the delay, I had to work out how to run the sudo query. I've managed to get these results:

eth0   Link encap: Ethernet  HWaddr 00:16:36:20:BC:EF
          inet addr:121.73.46.73 Bcast:121.73.46.255   Mask:255.255.255.0
          inet6 addr: fe88::216:36ff:fe20:bcef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19022 errors:0 dropped:0 overruns:0 frame:0
          TX pac kets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1143106 (1.0 MiB)  TX bytes:3661 (3.5 KiB)
          Interrupt:16 Base address:0x1800

lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:692 (692.0 b)  TX bytes:692 (692.0 b)

Is this of any help? Look forward to hearing from you and thanks in anticipation, best regards

Jim Lee

---

