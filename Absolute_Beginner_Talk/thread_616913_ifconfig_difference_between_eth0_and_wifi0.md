---
title: "ifconfig difference between eth0 and wifi0"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by teryowen on 2007-11-18
I type this command in "ifconfig" and get the following:

```

ath0      Link encap:Ethernet  HWaddr 00:11:95:BC:B6:02  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:febc:b602/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:158942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:227289688 (216.7 MB)  TX bytes:8025115 (7.6 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:F2:6F:32:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14600 (14.2 KB)  TX bytes:14600 (14.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-BC-B6-02-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:215291 errors:0 dropped:0 overruns:0 frame:37386
          TX packets:93221 errors:98 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:239810656 (228.7 MB)  TX bytes:10843593 (10.3 MB)
          Interrupt:20 

```

What is the difference between wifi0 and ath0? just wondering.

---

### Post by TalioGladius on 2007-11-18
Not sure what the unspec encapsulation is.  What returns when you run an iwconfig?

---

### Post by teryowen on 2007-11-18
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Disera"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:18:39:50:6E:98   
          Bit Rate:18 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-49 dBm  Noise level=-95 dBm
          Rx invalid nwid:7316  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

the thing is when i run "ifconfig wifi0 down" my wireless stops working

---

