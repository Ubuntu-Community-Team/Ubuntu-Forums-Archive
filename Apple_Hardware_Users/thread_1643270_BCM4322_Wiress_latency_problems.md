---
title: "BCM4322 Wiress latency problems"
date: 2010-12-11
forum: Apple Hardware Users
---

### Post by TP2k on 2010-12-11
Hi All,

I have a MCB4322 Wireless card in a Macbook Pro (5,5) and I am experiencing high latency such that ssh sessions are noticeably laggy. For example:

```

PING www.l.google.com (173.194.37.104) 56(84) bytes of data.
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=1 ttl=58 time=14.5 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=2 ttl=58 time=140 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=3 ttl=58 time=51.5 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=4 ttl=58 time=172 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=5 ttl=58 time=79.3 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=6 ttl=58 time=16.1 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=7 ttl=58 time=18.4 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=8 ttl=58 time=16.1 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=9 ttl=58 time=15.7 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=10 ttl=58 time=16.3 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=11 ttl=58 time=377 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=12 ttl=58 time=108 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=13 ttl=58 time=14.6 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=14 ttl=58 time=139 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=15 ttl=58 time=42.0 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=16 ttl=58 time=171 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=17 ttl=58 time=88.0 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=18 ttl=58 time=16.5 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=19 ttl=58 time=17.5 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=20 ttl=58 time=13.7 ms

--- www.l.google.com ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19027ms
rtt min/avg/max/mdev = 13.764/76.573/377.208/88.453 ms
```
As you can see, there are spikes of large latency. This is using the 'wl' driver provided from the 'bcmwl-kernel-source' package. Running Ubuntu 10.04.

Under OSX I do not get the same problems:

```

PING www.l.google.com (173.194.36.104): 56 data bytes
64 bytes from 173.194.36.104: icmp_seq=0 ttl=58 time=16.137 ms
64 bytes from 173.194.36.104: icmp_seq=1 ttl=58 time=14.638 ms
64 bytes from 173.194.36.104: icmp_seq=2 ttl=58 time=15.960 ms
64 bytes from 173.194.36.104: icmp_seq=3 ttl=58 time=17.319 ms
64 bytes from 173.194.36.104: icmp_seq=4 ttl=58 time=15.098 ms
64 bytes from 173.194.36.104: icmp_seq=5 ttl=58 time=14.403 ms
64 bytes from 173.194.36.104: icmp_seq=6 ttl=58 time=13.964 ms
64 bytes from 173.194.36.104: icmp_seq=7 ttl=58 time=14.167 ms
64 bytes from 173.194.36.104: icmp_seq=8 ttl=58 time=15.997 ms
64 bytes from 173.194.36.104: icmp_seq=9 ttl=58 time=14.357 ms
64 bytes from 173.194.36.104: icmp_seq=10 ttl=58 time=14.633 ms
64 bytes from 173.194.36.104: icmp_seq=11 ttl=58 time=16.642 ms
64 bytes from 173.194.36.104: icmp_seq=12 ttl=58 time=16.146 ms
64 bytes from 173.194.36.104: icmp_seq=13 ttl=58 time=15.903 ms
64 bytes from 173.194.36.104: icmp_seq=14 ttl=58 time=16.563 ms
64 bytes from 173.194.36.104: icmp_seq=15 ttl=58 time=16.005 ms
64 bytes from 173.194.36.104: icmp_seq=16 ttl=58 time=14.421 ms
64 bytes from 173.194.36.104: icmp_seq=17 ttl=58 time=16.424 ms
64 bytes from 173.194.36.104: icmp_seq=18 ttl=58 time=16.345 ms
64 bytes from 173.194.36.104: icmp_seq=19 ttl=58 time=16.305 ms

--- www.l.google.com ping statistics ---
20 packets transmitted, 20 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 13.964/15.571/17.319/0.975 ms


```Things I have tried:

[LIST]
[*]Turning off power management (i.e. iwconfig eth1 power off)
[*]Running 64bit distro instead of 32bit
[*]Building the latest driver from the Broadcom site and used that instead of the packaged version (v5.60.246.6)
[*]Tried other access points incase it was a compatibility quirk.
[/LIST]
None of the above have made any difference. I also attempted to use the windows driver from the Apple Install CD via ndiswrapper, but failed.

Does anyone else have any ideas of what may be causing the problem?

Thanks,
Dan.

---

### Post by luddek on 2010-12-26
I'm experiencing the same problems. A reload of the kernel module seems to solve it temporarily for me but the problem comes back after a while.

```
sudo modprobe -r wl && sleep 5 && sudo modprobe wl
```
EDIT: Found a fix here [https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Proprietary](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Proprietary)

---

### Post by TP2k on 2011-01-12
Hi,

I'm glad you found the solution for your problem, although it doesn't work for me.

I have found out that during the second of high latency the card attempts to use 802.11n (i.e. iwconfig eth1 shows "Frequency:5.xxx GHz"). The current WAP I'm using to test only supports 802.11b/g.

I am not particularly bothered about wireless-n support, does anyone know how to disable it?

Thanks,
Dan.

---

