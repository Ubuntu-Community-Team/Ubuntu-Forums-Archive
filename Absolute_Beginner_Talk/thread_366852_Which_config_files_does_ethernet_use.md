---
title: "Which config files does ethernet use?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by ramzai on 2007-02-21
After few experiments (trying to make my wireless work) I've (sadly) lost my ethernet connection. I have tried quite a bit, but couldn't locate the source of my problem.

I have my Ethernet card working ok under WinXP and (more important) on my Edgy Live/Install CD. So if I find the diff between working and broken system, I'll be able to solve the problem. So I'm asking for your help - what can go wrong (in config)?

Here is some information about my (broken) config:
```
ramzai@ramzai-laptop:~$ dmesg | grep eth
[    3.792000] eth0: Broadcom 4400 10/100BaseT Ethernet [MAC-address hidden]
[   21.700000] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[   23.096000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.704000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   24.704000] b44: eth0: Flow control is off for TX and off for RX.
[   24.704000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.872000] eth0: no IPv6 routers present
[   42.204000] device eth0 entered promiscuous mode
[   42.204000] audit(1172077377.077:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
ramzai@ramzai-laptop:~$ lspci | grep eth
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
ramzai@ramzai-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr [MAC-address hidden]
          inet addr:172.16.32.34  Bcast:172.16.32.255  Mask:255.255.255.0
          inet6 addr: [inet6 addr hidden] Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6317 errors:422 dropped:203 overruns:0 frame:1
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:695702 (679.3 KiB)  TX bytes:28208 (27.5 KiB)
          Interrupt:22

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12931 (12.6 KiB)  TX bytes:12931 (12.6 KiB)

ramzai@ramzai-laptop:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.32.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         172.16.32.3     0.0.0.0         UG    0      0        0 eth0
ramzai@ramzai-laptop:~$ cat /proc/net/dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:   20701     212    0    0    0     0          0         0    20701     212    0    0    0     0       0          0
  eth0:  695702    6317  **422**  **203**    0     1          0       104    28208     267    0    0    0     0       0          0
ramzai@ramzai-laptop:~$ cat /proc/interrupts | grep eth
 22:       5980          0   IO-APIC-fasteoi   eth0
ramzai@ramzai-laptop:~$ ping 172.16.32.3
PING 172.16.32.3 (172.16.32.3) 56(84) bytes of data.
From 172.16.32.34 icmp_seq=1 Destination Host Unreachable
From 172.16.32.34 icmp_seq=2 Destination Host Unreachable
From 172.16.32.34 icmp_seq=3 Destination Host Unreachable
From 172.16.32.34 icmp_seq=5 Destination Host Unreachable
From 172.16.32.34 icmp_seq=6 Destination Host Unreachable

--- 172.16.32.3 ping statistics ---
7 packets transmitted, 0 received, +5 errors, 100% packet loss, time 6016ms
, pipe 3
``` 
172.16.32.3 is my gateway that I'm trying to ping. Also please note the number of errors in /proc/net/dev

Thank you in advance!

---

### Post by Jussi Kukkonen on 2007-02-21
Basically just */etc/network/interfaces* (see *man interfaces*).

---

### Post by ramzai on 2007-02-21
> **Jussi Kukkonen said:**
> Basically just */etc/network/interfaces* (see *man interfaces*).
Thanks, Jussi! Comparing diff and reading man helped me to solve the problem. Thanks again!

---

