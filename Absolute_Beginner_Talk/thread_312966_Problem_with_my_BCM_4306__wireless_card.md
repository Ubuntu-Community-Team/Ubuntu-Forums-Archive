---
title: "Problem with my BCM 4306  wireless card"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by gcziprusz on 2006-12-05
Hi I just installed Ubuntu 6.10 on my compaq LAptop Its a dual boot for now since Im new to linux.
The install went fine but I cannot connect to the internet via my broadcom wireless card. The ethernet wired connection works fine.
I managed to install the ndiswrapper following this thread
[www.ubuntuforums.org/showthread.php?t=201902](www.ubuntuforums.org/showthread.php?t=201902)
below I copied my outputs from ifconfig and iwconfig
At home I have WPA but Im in school now and it still do not connect.
I enabled the wireless connection.in System/asdministration/networking

I know I have to be pretty close but its driving me crazy!!:confused: 
Can Someone Help with this please?

gcziprusz@gabe-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

gcziprusz@gabe-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:22:D2:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:55:29:9D  
          inet6 addr: fe80::290:4bff:fe55:299d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1460 (1.4 KiB)  TX bytes:468 (468.0 b)
          Interrupt:217 Memory:e8100000-e8102000

---

