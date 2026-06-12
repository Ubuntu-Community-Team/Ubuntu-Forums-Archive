---
title: "Asus Eee PC T101MT wireless network does not work"
date: 2011-12-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Septi on 2011-12-15
I installed Oneiric Ocelot on the Asus Ebut now I can't ee PC T101MT, but now I can't access the internet. I connected via wireless network, and network applet, as well as ifconfig, says everything is fine. However, I can neither resolve google.com, nor even ping the router, which is at 192.168.0.1:
> septi@septi-T101MT:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:36:6d:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:72:a8:60  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76f0:6dff:fe72:a860/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60464 (60.4 KB)  TX bytes:18863 (18.8 KB)

septi@septi-T101MT:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Network25715"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 1C:AF:F7:44:2E:7E   
          Bit Rate=40.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:0

septi@septi-T101MT:~$ ping google.com
ping: unknown host google.com
septi@septi-T101MT:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
^C
--- 192.168.0.1 ping statistics ---
29 packets transmitted, 0 received, 100% packet loss, time 28223ms The funny thing is that network worked very fine during installation (updates were downloaded successfully). But now I have to boot into that sluggish microsoft thingy to post this question :(

Anyone can help?

---

### Post by Cigue on 2012-01-09
I've got the exact same problem, It's a bit disconcerting.

---

