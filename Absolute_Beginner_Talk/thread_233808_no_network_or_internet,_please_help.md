---
title: "no network or internet, please help"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by frustrated on 2006-08-10
I'm new to Ubuntu and am trying to get connected to the internet.  I have a dlink router that is connecting to a Motorola SB4200 cable modem.  I have a windows machine and a mac on my network now and had a Fedora linux machine on it before.  I didn't like Fedora so I'm trying to switch to Ubuntu but I can't seem to connect to the network with it.  When I do an ifconfig this is what I get:

eth0      Link encap:Ethernet  HWaddr 00:08:A1:14:D5:F5
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe14:d5f5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:185 errors:84 dropped:0 overruns:0 frame:2
          TX packets:17 errors:3 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000
          RX bytes:55044 (53.7 KiB)  TX bytes:1402 (1.3 KiB)
          Interrupt:169 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

I tried setting my connection up manually using the network settings manager and setting up a static ip address for the machine but I can't even connect to my router even though it's hard wired in using an ethernet cable.

Please help, I really want to use Ubuntu but at this rate it's not looking good.

---

### Post by steve.horsley on 2006-08-10
It looks like you have an IP address that looks sensible. Can you try these 3 commands?
> route
cat /etc/resolv.conf
ping 192.168.0.1
I'm guessing the router address there.

---

### Post by frustrated on 2006-08-10
ok this is what I got...

jrodda@Ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
jrodda@Ubuntu:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
jrodda@Ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.104 icmp_seq=1 Destination Host Unreachable
From 192.168.0.104 icmp_seq=2 Destination Host Unreachable
From 192.168.0.104 icmp_seq=3 Destination Host Unreachable
From 192.168.0.104 icmp_seq=5 Destination Host Unreachable
From 192.168.0.104 icmp_seq=6 Destination Host Unreachable
From 192.168.0.104 icmp_seq=7 Destination Host Unreachable
From 192.168.0.104 icmp_seq=9 Destination Host Unreachable
From 192.168.0.104 icmp_seq=10 Destination Host Unreachable
From 192.168.0.104 icmp_seq=11 Destination Host Unreachable
From 192.168.0.104 icmp_seq=13 Destination Host Unreachable
From 192.168.0.104 icmp_seq=14 Destination Host Unreachable
From 192.168.0.104 icmp_seq=15 Destination Host Unreachable
From 192.168.0.104 icmp_seq=17 Destination Host Unreachable
From 192.168.0.104 icmp_seq=18 Destination Host Unreachable
From 192.168.0.104 icmp_seq=19 Destination Host Unreachable
From 192.168.0.104 icmp_seq=21 Destination Host Unreachable
From 192.168.0.104 icmp_seq=22 Destination Host Unreachable
From 192.168.0.104 icmp_seq=23 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
26 packets transmitted, 0 received, +18 errors, 100% packet loss, time 25010ms
, pipe 3

any ideas??

---

### Post by frustrated on 2006-08-10
correction, I forgot that I had unplugged my cable.  This is what I get...

jrodda@Ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface192.168.0.0     *               255.255.255.0   U     0      0        0 eth0default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0jrodda@Ubuntu:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
jrodda@Ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=0.966 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=0.925 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=0.829 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=1.01 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=0.758 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=127 time=0.956 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=127 time=0.992 ms
From 192.168.0.104 icmp_seq=49 Destination Host Unreachable
From 192.168.0.104 icmp_seq=50 Destination Host Unreachable
From 192.168.0.104 icmp_seq=52 Destination Host Unreachable
From 192.168.0.104 icmp_seq=53 Destination Host Unreachable
From 192.168.0.104 icmp_seq=56 Destination Host Unreachable
From 192.168.0.104 icmp_seq=57 Destination Host Unreachable
From 192.168.0.104 icmp_seq=60 Destination Host Unreachable
From 192.168.0.104 icmp_seq=63 Destination Host Unreachable
From 192.168.0.104 icmp_seq=64 Destination Host Unreachable
From 192.168.0.104 icmp_seq=65 Destination Host Unreachable
From 192.168.0.104 icmp_seq=66 Destination Host Unreachable
From 192.168.0.104 icmp_seq=67 Destination Host Unreachable
From 192.168.0.104 icmp_seq=69 Destination Host Unreachable
From 192.168.0.104 icmp_seq=70 Destination Host Unreachable
From 192.168.0.104 icmp_seq=73 Destination Host Unreachable
From 192.168.0.104 icmp_seq=74 Destination Host Unreachable
From 192.168.0.104 icmp_seq=75 Destination Host Unreachable
From 192.168.0.104 icmp_seq=76 Destination Host Unreachable
From 192.168.0.104 icmp_seq=77 Destination Host Unreachable
From 192.168.0.104 icmp_seq=78 Destination Host Unreachable
From 192.168.0.104 icmp_seq=79 Destination Host Unreachable
From 192.168.0.104 icmp_seq=80 Destination Host Unreachable
From 192.168.0.104 icmp_seq=83 Destination Host Unreachable
From 192.168.0.104 icmp_seq=84 Destination Host Unreachable
From 192.168.0.104 icmp_seq=87 Destination Host Unreachable
From 192.168.0.104 icmp_seq=89 Destination Host Unreachable
From 192.168.0.104 icmp_seq=90 Destination Host Unreachable
From 192.168.0.104 icmp_seq=91 Destination Host Unreachable
From 192.168.0.104 icmp_seq=93 Destination Host Unreachable
From 192.168.0.104 icmp_seq=94 Destination Host Unreachable
From 192.168.0.104 icmp_seq=95 Destination Host Unreachable
From 192.168.0.104 icmp_seq=98 Destination Host Unreachable
From 192.168.0.104 icmp_seq=99 Destination Host Unreachable
From 192.168.0.104 icmp_seq=103 Destination Host Unreachable
From 192.168.0.104 icmp_seq=105 Destination Host Unreachable
From 192.168.0.104 icmp_seq=106 Destination Host Unreachable
From 192.168.0.104 icmp_seq=107 Destination Host Unreachable
From 192.168.0.104 icmp_seq=108 Destination Host Unreachable
From 192.168.0.104 icmp_seq=109 Destination Host Unreachable
From 192.168.0.104 icmp_seq=110 Destination Host Unreachable
From 192.168.0.104 icmp_seq=113 Destination Host Unreachable
From 192.168.0.104 icmp_seq=114 Destination Host Unreachable
From 192.168.0.104 icmp_seq=115 Destination Host Unreachable
From 192.168.0.104 icmp_seq=116 Destination Host Unreachable
From 192.168.0.104 icmp_seq=118 Destination Host Unreachable
From 192.168.0.104 icmp_seq=119 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
120 packets transmitted, 7 received, +46 errors, 94% packet loss, time 119549ms
rtt min/avg/max/mdev = 0.758/0.919/1.010/0.090 ms, pipe 3
jrodda@Ubuntu:~$

---

### Post by steve.horsley on 2006-08-11
OK. You have a good route, and a good DNS resolution entry. You should be able to connect to the router since you can ping it. What makes you say you can't connect to it?

We know you can ping the router. Let's see if you can ping through it to the internet. Try:
**ping 82.211.81.186**
If that works, let's try it using DNS:
**ping [www.ubuntuforums.org](www.ubuntuforums.org)**
If that works. let's try reaching the HTTP port:
[B]telnet [www.ubuntuforums.org](www.ubuntuforums.org) 80
GET /[/B]
If that works then so should firefox etc. Sorry the www stuff comes out in brown. I can't get the sodding thing to stop putting url tags round them.

Post any errors you get.

---

### Post by AxeNsmash on 2006-10-24
couldn't connect to the internet and then found this thread 
just wanted you to know it helped me greatly 


thanks steve.horsley


AxeNsmash

---

### Post by LookTJ on 2006-10-24
try this in firefox:

1. go here

```
about:config
```

2. find

```
network.dns.disableIPv6
```

and set value to

```
**true**
```

---

