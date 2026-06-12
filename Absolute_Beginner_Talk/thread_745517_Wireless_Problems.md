---
title: "Wireless Problems"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by spazzywulf on 2008-04-04
I'm having wireless issues. The wireless worked well for a while, but then crashed and no all it does is just loop trying to connect.  I think it's a chipset error but I don't know how to fix it. Any help would be appriciated



rebecca@rebecca-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

---

### Post by neurostu on 2008-04-04
what do you get when you type (in a terminal)
```

ifconfig

```

Also have you tried rebooting?

---

### Post by spazzywulf on 2008-04-04
rebecca@rebecca-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:18:9A:01  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe18:9a01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2980969 (2.8 MB)  TX bytes:255282 (249.2 KB)
          Interrupt:19 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:68:B5:C4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2730 (2.6 KB)
          Interrupt:3 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by Crafty Kisses on 2008-04-04
You should try pinging a website, do the following:
```
ping google.com
```
See if you receive any packets back.

---

### Post by spazzywulf on 2008-04-04
This is what came up,but i'm connected by a wire so I don't know if that matters.

rebecca@rebecca-laptop:~$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=240 time=85.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=240 time=89.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=240 time=89.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=4 ttl=240 time=94.5 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=5 ttl=240 time=86.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=6 ttl=240 time=88.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=7 ttl=240 time=88.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=8 ttl=240 time=85.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=9 ttl=240 time=95.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=10 ttl=240 time=88.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=11 ttl=240 time=94.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=12 ttl=240 time=85.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=13 ttl=240 time=88.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=14 ttl=240 time=88.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=15 ttl=240 time=90.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=16 ttl=240 time=88.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=17 ttl=240 time=95.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=18 ttl=240 time=89.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=19 ttl=240 time=85.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=20 ttl=240 time=89.3 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=21 ttl=240 time=94.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=22 ttl=240 time=89.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=23 ttl=240 time=94.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=24 ttl=240 time=89.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=25 ttl=240 time=89.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=26 ttl=240 time=85.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=27 ttl=240 time=88.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=28 ttl=240 time=88.5 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=29 ttl=240 time=89.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=30 ttl=240 time=85.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=31 ttl=240 time=88.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=32 ttl=240 time=88.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=33 ttl=240 time=85.5 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=34 ttl=240 time=88.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=35 ttl=240 time=89.3 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=36 ttl=240 time=88.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=37 ttl=240 time=94.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=38 ttl=240 time=87.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=39 ttl=240 time=84.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=40 ttl=240 time=88.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=41 ttl=240 time=89.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=42 ttl=240 time=84.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=43 ttl=240 time=85.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=44 ttl=240 time=94.3 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=45 ttl=240 time=85.5 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=46 ttl=240 time=89.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=47 ttl=240 time=90.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=48 ttl=240 time=89.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=49 ttl=240 time=88.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=50 ttl=240 time=94.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=51 ttl=240 time=94.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=52 ttl=240 time=88.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=53 ttl=240 time=86.3 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=54 ttl=240 time=88.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=55 ttl=240 time=85.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=56 ttl=240 time=85.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=57 ttl=240 time=85.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=58 ttl=240 time=88.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=59 ttl=240 time=85.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=60 ttl=240 time=88.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=61 ttl=240 time=88.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=62 ttl=240 time=89.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=63 ttl=240 time=88.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=64 ttl=240 time=88.2 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=65 ttl=240 time=89.3 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=66 ttl=240 time=88.3 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=67 ttl=240 time=95.5 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=68 ttl=240 time=85.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=69 ttl=240 time=89.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=70 ttl=240 time=89.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=71 ttl=240 time=85.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=72 ttl=240 time=85.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=73 ttl=240 time=85.5 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=74 ttl=240 time=88.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=75 ttl=240 time=88.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=76 ttl=240 time=94.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=77 ttl=240 time=88.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=78 ttl=240 time=85.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=79 ttl=240 time=88.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=80 ttl=240 time=84.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=81 ttl=240 time=89.1 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=82 ttl=240 time=89.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=83 ttl=240 time=88.8 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=84 ttl=240 time=89.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=85 ttl=240 time=94.3 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=86 ttl=240 time=88.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=87 ttl=240 time=94.4 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=88 ttl=240 time=88.5 ms

--- google.com ping statistics ---
88 packets transmitted, 88 received, 0% packet loss, time 87207ms
rtt min/avg/max/mdev = 84.789/88.916/95.514/2.923 ms

---

### Post by neurostu on 2008-04-04
try disconnecting the ethernet connection when you run that command.

---

### Post by northern lights on 2008-04-04
If you're on a wired connection, the ping output doesn't mean a thing, unfortunately.

> **spazzywulf said:**
> rebecca@rebecca-laptop:~$ lspci
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Anyways, the Broadcom BCM43xx chipsets been a problem under linux since Lord knows when. Try using ndiswrapper. Googling or forum searching should yield many tutorials. You could also start [here]("http://ubuntuforums.org/showthread.php?t=588888")

---

### Post by bt224 on 2008-04-04
I've been working with an old Linksys card (R8180 chip) for years, couldn't get it to go with 8.04. I got tired of fighting with it on every upgrade. I picked up an Edimax at newegg for $15, worked right out of the box. Wish I had done this a couple of years ago. Just a suggestion, I have no connection with either.

---

### Post by nashgill on 2008-04-04
I spent hours getting a broadcom card working last night!  Ugh!
Have you enabled the restricted driver?

---

