---
title: "Verizon DSL wireless not working"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-11-04
OK... Managed to get the thing working through a cat-5, but my settings must be wrong somewhere. I know my drivers are good, as the wireless works through my Linksys router. I need someone to help me find the other places where settings get changed. (Sorry, I forgot!)

I have gone to the System > Admin > Networking, As well as the network tools. Though the "tools" is like Greek to me... Oops... I mean Arabic... I'm OK with Greek... LOL

EDIT: I cannot get Networking to activate my eth0 either... I have to re-boot, and it finds it then. My wireless is designated eth1

---

### Post by Papa-san on 2006-11-04
```
john@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:192.168.1.45  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fee1:ba40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2543 errors:0 dropped:0 overruns:1 frame:0
          TX packets:1490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:769219 (751.1 KiB)  TX bytes:206687 (201.8 KiB)
          Interrupt:11 Base address:0xec00

eth1      Link encap:Ethernet  HWaddr 00:90:4B:2C:52:6B
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:f8ffc000-f8ffe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3088 (3.0 KiB)  TX bytes:3088 (3.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
```
john@laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid 06B408770040
wireless-key XXXX-XXXX-XX

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid ubuntu
wireless-key XXXX-XXXX-XX






auto eth0

```
```
john@laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by Papa-san on 2006-11-04
No help?

OK... Where and how do I edit whatever file has that info (old ESSID and WEP) so it will actually change?

---

### Post by Papa-san on 2006-11-04
In my network tools, I get the name 'eth1' in thr drop-down, but when I highlight that choice, it only gives my 'IPv6' (plus address); netmask 64; Scope: link
The configure button doesn't become clickable, either.

---

