---
title: "Network Problem"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by OffHand on 2006-03-16
Hi
I cannot get to use Ubuntu as a gateway to get online with my Mac.
I got 2 ethernet cards. The one connected to my modem uses dhcp and works fine. My other card (connected with my mac using a crosscable) has a manual ip adress 192.168.0.1 subnet 255.255.255.0. My Mac has ip adress 192.168.0.2 subnet 255.255.255.0 andd router and dns are 192.168.0.1. Still sharing doesn't work. I can ping the computers both ways. 

This is the output of ifconfig:
admin@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:A7:07:B8:09
          inet addr:xx.xx.xxx.xx  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::210:a7ff:fe07:b809/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11644716 (11.1 MiB)  TX bytes:521966 (509.7 KiB)
          Interrupt:5 Base address:0xef00

eth1      Link encap:Ethernet  HWaddr 00:40:F4:6A:C6:AA
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe6a:c6aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9230 (9.0 KiB)  TX bytes:10812 (10.5 KiB)
          Interrupt:10 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4608 (4.5 KiB)  TX bytes:4608 (4.5 KiB)



Hope anyone can help me. Thanks in advance!

---

### Post by OffHand on 2006-03-16
Solved it with this guide: 

[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

Thread closed.

---

