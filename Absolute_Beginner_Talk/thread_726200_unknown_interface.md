---
title: "unknown interface"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by March20 on 2008-03-16
Can somebody please have a look at the following output and tell me what could be wrong, and how could i fix it. Thank you

superman@smallville:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:CF:9E:D6:13  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:336332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:216269228 (206.2 MB)  TX bytes:24491553 (23.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:9C:5A:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:16:36:9C:5A:47  
          inet addr:169.254.5.34  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7128 (6.9 KB)  TX bytes:7128 (6.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-9E-D6-13-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:457625 errors:0 dropped:0 overruns:0 frame:7839
          TX packets:172923 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:143865361 (137.2 MB)  TX bytes:29698022 (28.3 MB)
          Interrupt:18 

superman@smallville:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"March20"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:60:B3:F8:F9:6B   
          Bit Rate:36 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-59 dBm  Noise level=-96 dBm
          Rx invalid nwid:181221  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

superman@smallville:~$

---

### Post by Ub1476 on 2008-03-16
Please post using the #: code tag.:)

Are you trying to get wireless working?

---

### Post by March20 on 2008-03-17
Everything is working, but i notice that the ath0,wifi0, and then there are other devices too... im using a laptop. Now im confused to which device is which.

---

### Post by PeterJS on 2008-03-17
Ath0 is a wireless card with an atheros chipset, eth0 is your wired connection, eth0:avahi is a virtual interface on your wired connection that has a self assigned address from avahi, lo is the loopback interface (ie 127.0.0.1), and wifi0 I belive that's the naming scheme madwifi uses, and given that it has no wireless extensions as shown by iwconfig it's probably a configuration fluke and doesn't exist.

---

