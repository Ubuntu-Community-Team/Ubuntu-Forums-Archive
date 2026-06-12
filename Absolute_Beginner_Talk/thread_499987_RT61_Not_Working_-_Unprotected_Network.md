---
title: "RT61 Not Working - Unprotected Network"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by 3ch0_z3r0 on 2007-07-13
Hello,

I posted this also in Networking, but I am a real Linux newbie, so it's difficult for me.
I thought I'd post it here also, as it may be easier for me.

I have a Conceptronic 54G powered by the Ralink RT61 Chipset.
I run Ubuntu 7 (latest), it detects my card + the network, but the icon spins around and cannot connect.

It is a DHCP network with no WEP/WPA Protection (Open Network)
In the other thread I was told to get this information as it may help:

```
ultima@ultima:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:13:33:18   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level:-70 dBm  Noise level:-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ultima@ultima:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:CE:B0:3E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7104 (6.9 KiB)  TX bytes:7104 (6.9 KiB)

ra1       Link encap:Ethernet  HWaddr 00:80:5A:38:B2:7A  
          inet6 addr: fe80::280:5aff:fe38:b27a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000 
          RX bytes:76962 (75.1 KiB)  TX bytes:1360 (1.3 KiB)
          Interrupt:20 

```

---

### Post by 3ch0_z3r0 on 2007-07-13
Anyone?

---

### Post by feelie88 on 2007-07-19
did you get any help

---

