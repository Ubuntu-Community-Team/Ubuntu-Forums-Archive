---
title: "iMac G5 (PPC). Can't see any wireless network"
date: 2008-08-25
forum: Apple Hardware Users
---

### Post by HydroxyMethylRadical on 2008-08-25
Running Hardy (8.04) on PowerPC iMac I got problem with wireless card.
lspci shows that it's "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)". I've already tried using fwcutter to make it work but it doesn't :(. In the most part of forum posts concerning this problem it can be solved with ndiswrapper, but I guess i can't use it because of different CPU.
What else can I try?

here is ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:11:24:39:c0:12  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:24ff:fe39:c012/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3006556 (2.8 MB)  TX bytes:279170 (272.6 KB)
          Interrupt:40 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49200 (48.0 KB)  TX bytes:49200 (48.0 KB)

```
and iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` 
listings.
I'm not quite sure (I'm amateur in Linux :)) but iwconfig shows that it works but I can't see my home wireless network or connect to it manually configuring essid and so on.

---

### Post by HydroxyMethylRadical on 2008-08-28
Any suggestions?

---

