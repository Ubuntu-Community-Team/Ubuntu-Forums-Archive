---
title: "The Very Bad Cat strikes again"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by DrTaylor on 2007-08-02
This time she's completely disabled my networking. Can't get online through either wired or wireless. Wireless networks don't show up and the wired network can't access anything - I plug it in, it shows up, and then I can't go anywhere or find any pages. The cable is the one for my XBox and I know it works and the port has never given me any problems, before you ask. Also, I live in the basement so I really need to have the wireless working anyway.

How do you lock/unlock the keyboard? If I forget to turn off my computer horrible things happen while I'm at work.

---

### Post by nick_h on 2007-08-02
To lock the screen use Ctrl+Alt+L, or you can get to it from the shutdown menu.

---

### Post by DrTaylor on 2007-08-02
Great. Any idea what she did to my internet?

---

### Post by nick_h on 2007-08-02
What output do you get from *ifconfig* and *iwconfig*?

---

### Post by DrTaylor on 2007-08-02
ifconfig is :
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:AD:AF:38  
          inet addr:192.168.0.69  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fead:af38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2716 (2.6 KiB)  TX bytes:5663 (5.5 KiB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:B5:52:EF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:d6000000-d6004000 

eth1:avah Link encap:Ethernet  HWaddr 00:14:A5:B5:52:EF  
          inet addr:169.254.9.113  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:d6000000-d6004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1292 (1.2 KiB)  TX bytes:1292 (1.2 KiB)

And iwconfig is:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I'm on the wired network, which is now suddenly working Thank God for small favors.

---

### Post by nick_h on 2007-08-02
It's good that at least your wired LAN is working now.

You could try:
```
iwlist eth1 scan
```
and see if you pick up any access points

---

### Post by DrTaylor on 2007-08-02
no scan results

---

### Post by nick_h on 2007-08-02
Have you tried re-booting your access point / router?

---

### Post by DrTaylor on 2007-08-02
It still doesn't see any networks. It doesn't see ours or they guy's next door.

---

### Post by nick_h on 2007-08-02
Your iwconfig output looks similar to mine.  I'm not a networking expert, perhaps someone else may be able to help.

---

### Post by DrTaylor on 2007-08-04
Okay, I've been working constantly for two days but now I have 15 hours until I have to go back so can someone help me!!!!????

---

