---
title: "help me!wireless router dlink dsl-g624t ubuntu 7.10 doesn't go"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by viva_linux on 2008-02-06
hi!
using network manager and wicd too, I can't go on internet wireless with my ubuntu 7.10.
I insert the right wap password, and I tried to change dns also (either the ones by my provider and the ones open).

Plese help me!

here I paste the result of some command from terminal:
[COLOR="Red"]Result of iwconfig:[/COLOR]lo        no wireless extensions.
eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"DLINK_WIRELESS"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:36 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-58 dBm  Noise level=-92 dBm
          Rx invalid nwid:1055  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

laptop:~$ 


[COLOR="red"]Result of ifconfig -a:[/COLOR]
ath0      Link encap:Ethernet  HWaddr 00:14:A4:0F:62:6E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe0f:626e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:55 dropped:55 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3966 (3.8 KB)  TX bytes:15063 (14.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:AC:E0:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14072 (13.7 KB)  TX bytes:14072 (13.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-A4-0F-62-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5955 errors:0 dropped:0 overruns:0 frame:67809
          TX packets:524 errors:2 dropped:55 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:653935 (638.6 KB)  TX bytes:42682 (41.6 KB)
          Interrupt:22

---

### Post by ubutufan on 2008-02-06
could you please post the contents of the file

/etc/network/interfaces

---

### Post by viva_linux on 2008-02-06
This is the content of [COLOR="Red"]/etc/network/interfaces[/COLOR]:

auto lo
iface lo inet loopback

Thank you.

---

