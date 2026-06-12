---
title: "10 min and it is all gone, HELP"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-06-07
**[B]**[/B]
hei
I am running on a dapper with adsl internet connection thru a router. After around 10 min my internet connection is down, I do not know why, it seems to be sending and reciveing packages. I you need more info just tell me what to write in the terminal, I am new to linux.  I have about 5 min before my connection will be down and have to restart, then maybe it will connect again for 10 min. 

thanks
__:

---

### Post by richbarna on 2006-06-07
Try disabling IPv6
> # mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
# depmod -a
I had this with a friends Ubuntu box.
I have the commands written on a peice of paper, I hope there aren't any typos ;)

EDIT: Someone else had this problem too and did this :-
> sudo gedit /etc/default/rcS 
and change either "UTC=no" or "UTC=yes"
Some people have changed NO to YES others have changed YES to NO and have solved their problems

I think there is also a bug report on this aswell :-  [Bug 333968]("https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/33968/+index")

---

### Post by wannabesurfer on 2006-06-08
I disabled the IPV6, and changed UTC to no, but still after now 15min the internet conection is down.

I run some checs in the terminal:
wannab:~$ pon dsl-provider
Plugin rp-pppoe.so loaded.
wannab:~$ plog
Jun  7 22:41:44 localhost pppd[6986]: Plugin rp-pppoe.so loaded.
Jun  7 22:41:44 localhost pppd[6988]: pppd 2.4.4b1 started by wannabe, uid 1000
wannab:~$ sudo mii-tool eth0
Password:
eth0: negotiated 100baseTx-FD, link ok
wannab:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:C0:15:29
          inet addr:10.0.0.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2a0:ccff:fec0:1529/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3661839 (3.4 MiB)  TX bytes:559131 (546.0 KiB)
          Interrupt:11 Base address:0x1400

wannab:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:C0:15:29
          inet addr:10.0.0.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2a0:ccff:fec0:1529/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3663139 (3.4 MiB)  TX bytes:559917 (546.7 KiB)
          Interrupt:11 Base address:0x1400

wannab:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.8.255.155   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.137      0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
wannab:~$ ping 10.0.0.137
PING 10.0.0.138 (10.0.0.137) 56(84) bytes of data.
64 bytes from 10.0.0.137: icmp_seq=1 ttl=255 time=3.61 ms
64 bytes from 10.0.0.137: icmp_seq=2 ttl=255 time=0.735 ms
64 bytes from 10.0.0.137: icmp_seq=3 ttl=255 time=0.711 ms
64 bytes from 10.0.0.137: icmp_seq=4 ttl=255 time=0.708 ms
64 bytes from 10.0.0.137: icmp_seq=5 ttl=255 time=0.719 ms
64 bytes from 10.0.0.137: icmp_seq=6 ttl=255 time=0.621 ms
64 bytes from 10.0.0.137: icmp_seq=7 ttl=255 time=0.724 ms
64 bytes from 10.0.0.137: icmp_seq=8 ttl=255 time=0.702 ms
64 bytes from 10.0.0.137: icmp_seq=9 ttl=255 time=0.699 ms
64 bytes from 10.0.0.137: icmp_seq=10 ttl=255 time=0.711 ms
64 bytes from 10.0.0.137: icmp_seq=11 ttl=255 time=0.711 ms
64 bytes from 10.0.0.137: icmp_seq=12 ttl=255 time=0.725 ms
64 bytes from 10.0.0.137: icmp_seq=13 ttl=255 time=0.616 ms
64 bytes from 10.0.0.137: icmp_seq=14 ttl=255 time=0.695 ms
64 bytes from 10.0.0.137: icmp_seq=15 ttl=255 time=0.712 ms
64 bytes from 10.0.0.137: icmp_seq=16 ttl=255 time=0.699 ms
64 bytes from 10.0.0.137: icmp_seq=17 ttl=255 time=0.722 ms
64 bytes from 10.0.0.137: icmp_seq=18 ttl=255 time=0.704 ms
64 bytes from 10.0.0.137: icmp_seq=19 ttl=255 time=0.700 ms
64 bytes from 10.0.0.137: icmp_seq=20 ttl=255 time=0.710 ms
64 bytes from 10.0.0.137: icmp_seq=21 ttl=255 time=0.698 ms

--- 10.0.0.138 ping statistics ---
21 packets transmitted, 21 received, 0% packet loss, time 20019ms
rtt min/avg/max/mdev = 0.616/0.839/3.614/0.622 ms
wannab:~$ ping 209.98.65.80
PING 209.98.65.80 (209.98.65.80) 56(84) bytes of data.

I tried the router on a different machine and it is working fine over longer period than my 10-15 minutes.

I hope to solve this thing, getting anoying to restart the machine all the time to connect to the internet.

---

