---
title: "Wireless trouble with latest Mini"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by xOrphenochx on 2009-01-22
I have one of the C2D 1.83ghz Mini. It looks like I have the adapter working with madwifi. But I can't get an IP address from this automatically. I notice that the iwconfig info for ath0 seems a bit random too. I'm at work so I only have SSH access right now and it's cabled. Unsecured hidden network.

```
lo        no wireless extensions.

 

eth0      no wireless extensions.

 

wifi0     no wireless extensions.

 

ath0      IEEE 802.11g  ESSID:"CoilDomain"  Nickname:""

          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated

          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1

          Retry:off   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm

          Rx invalid nwid:44990  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 

virbr0    no wireless extensions.

 

pan0      no wireless extensions.

 

 

eth0      Link encap:Ethernet  HWaddr 00:16:cb:b0:32:20

          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::216:cbff:feb0:3220/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:2428 errors:0 dropped:0 overruns:0 frame:0

          TX packets:430 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:564428 (564.4 KB)  TX bytes:46476 (46.4 KB)

          Interrupt:16

 

lo        Link encap:Local Loopback

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 

virbr0    Link encap:Ethernet  HWaddr 3a:c9:01:21:28:cf

          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0

          inet6 addr: fe80::38c9:1ff:fe21:28cf/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0

          RX bytes:0 (0.0 B)  TX bytes:14079 (14.0 KB)

 

wifi0     Link encap:UNSPEC  HWaddr 00-1F-F3-C5-14-56-00-00-00-00-00-00-00-00-00-00

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:44825 errors:0 dropped:0 overruns:0 frame:11353

          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:280

          RX bytes:4356994 (4.3 MB)  TX bytes:9384 (9.3 KB)

          Interrupt:17

```

---

