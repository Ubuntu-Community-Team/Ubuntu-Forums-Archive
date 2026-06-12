---
title: "Intermittent Internet Connectionissue"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-11
Hi All.
I'm having an issue with my install. For some reason my internet connection keeps dropping. I know the issue isn't with my router, becasue my 2 windows machines are not having any problems.
Sometime, like right now, it work perfectly. But at other time it fails to find any URLs. I've tried ping in the Networking tools applet and can ping my router (192.168.0.1) but cannot ping any www addresses.

Here's a copy of ifconfig if that helps.

eth0      Link encap:Ethernet  HWaddr 00:11:11:70:93:F5
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe70:93f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:639743 (624.7 KiB)  TX bytes:54926 (53.6 KiB)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:360 (360.0 b)  TX bytes:360 (360.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.156.1  Bcast:172.16.156.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.100.1  Bcast:172.16.100.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by rlozano on 2006-12-11
do you have your gateway properly setup and your DNS?

---

### Post by trav5 on 2006-12-11
It sounds like you are losing your dns. Check this out.[http://www.ubuntuforums.org/showthread.php?t=282034]("http://www.ubuntuforums.org/showthread.php?t=282034")

---

### Post by dkenny on 2006-12-11
> **trav5 said:**
> It sounds like you are losing your dns. Check this out.[http://www.ubuntuforums.org/showthread.php?t=282034]("http://www.ubuntuforums.org/showthread.php?t=282034")

Thanks for the link. One quetion thought - is this applicable for a situation like me where i have a router acting as a DNS server?

i.e should I edit the resolv.conf file and add TimeWarners Domain Name Servers or just add my routers address?

---

### Post by trav5 on 2006-12-12
> **dkenny said:**
> Thanks for the link. One quetion thought - is this applicable for a situation like me where i have a router acting as a DNS server?

i.e should I edit the resolv.conf file and add TimeWarners Domain Name Servers or just add my routers address?

I use the dns my isp(verizon) gave me in resolv.conf . Make sure you uncomment and put your dns in the line on dhclient.conf also or it will eventually overwrite your resolv.conf.

---

### Post by dkenny on 2006-12-12
Got it. Thanks

---

### Post by dkenny on 2006-12-12
Well, that looked like it was working but it started dropping connections again

eth0      Link encap:Ethernet  HWaddr 00:11:11:70:93:F5
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe70:93f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:**60803 errors**:0 dropped:0 overruns:0 frame:0
          TX packets:**47340 errors**:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72428467 (69.0 MiB)  TX bytes:6929089 (6.6 MiB)
          Interrupt:169

---

### Post by rlozano on 2006-12-12
please check too your layer 1 (physical connection). you may have all the settings correct but if your layer 1 is not working properly then it will wack your head off. ;-)

---

