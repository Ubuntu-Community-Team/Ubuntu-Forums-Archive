---
title: "Wired Ethernet on Mac Mini with ubuntu 16.04 not working"
date: 2016-07-05
forum: Apple Hardware Users
---

### Post by merlinsilk2 on 2016-07-05
I installed 16.04 as a double boot on my 2011 Mac Mini and all seemed to work - until I tried to connect to my network (wired and wireless). I got the message that the connection is established after quite a while, but no IPv4s were assigned assigned. I managed to get wireless working with
```
apt-get install firmware-linux-nonfree broadcom-sta-dkms
```
and when I look with ifconfig I get
```

enp2s0f0  Link encap:Ethernet  HWaddr 3c:07:54:0c:52:24
          inet6 addr: fdca:b917:47b7:0:1e7c:3665:dcdc:19fa/64 Scope:Global
          inet6 addr: fe80::9755:a66:e5b0:1981/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15904161 errors:0 dropped:83 overruns:0 frame:0
          TX packets:10501704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21284256869 (21.2 GB)  TX bytes:900062142 (900.0 MB)
          Interrupt:16

lo       ....

wlp3s0    Link encap:Ethernet  HWaddr 28:cf:da:05:ba:15
          inet addr:192.168.0.145  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fdca:b917:47b7:0:4427:de64:bc3:348e/64 Scope:Global
          inet6 addr: fdca:b917:47b7:0:1514:e1f0:42b9:b1b7/64 Scope:Global
          inet6 addr: fe80::873:b317:14d:2f60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1499590 errors:0 dropped:0 overruns:0 frame:274029
          TX packets:10336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:92169767 (92.1 MB)  TX bytes:7208660 (7.2 MB)
          Interrupt:17

```

The adapter is seen but only with IP6, it's probably not connecting to DHCP to get an IP.
Setting an IP manually does not help.

I tried to get the driver sources from Broadcom but failed miserably compiling (missing .h file) - kernel compilation is a bit beyond me, so I can't figure out what I might be missing there.

There must be something else - simpler - to solve this problem, there are so many mac minis out there and some of the owners should be tired of OSX and run linux!   :-)
 
Any help to get this going is very much appreciated.
Thanks - Merlin

---

### Post by merlinsilk2 on 2016-07-08
Am I really the very first one with this problem?   :-(

---

### Post by mfox on 2016-07-16
I have a 2012 mac mini with a Broadcom BCM57766 ethernet adapter. It worked out of the box with 16.04.  It was my wifi that wouldn't work out of the box. Do you have the same card in yours?

---

