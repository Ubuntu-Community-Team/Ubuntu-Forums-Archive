---
title: "HUGE problem with Macbook wireless"
date: 2008-05-21
forum: Apple Hardware Users
---

### Post by HuoMaKe on 2008-05-21
I have a Macbook with Ubuntu 8.04. It's been through 7.04, 7.10, and the 8.04 alphas and betas. Now that I've installed the full version of 8.04, though, the wireless has gotten to quitting out every half hour or so.

The problem is nearly irreversible once it happens. I have taken to just restarting the system whenever I notice. First, the connection just dies, then after a little bit it shows the wireless as having died. I have installed madwifi-ng (to get the wireless working in the first place), Wicd (to fix an issue I had with network-manager), and Wicd is presumably using Wext as opposed to madwifi, but whenever I update the kernel, I have to recompile Madwifi before the wireless will work.

I could use some help here. I've seen a few other posts but they seem to have been solved or forgotten. Someone let me know what info they need. I'll start with what I know how to do:


```
ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:1c:b3:b4:4f:ae  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:b3ff:feb4:4fae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22276198 (21.2 MB)  TX bytes:655337 (639.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:19:e3:45:a1:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113400 (110.7 KB)  TX bytes:113400 (110.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-B3-B4-4F-AE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23514 errors:0 dropped:0 overruns:0 frame:590
          TX packets:6475 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:12803007 (12.2 MB)  TX bytes:801605 (782.8 KB)
          Interrupt:16 




iwconfig:

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:BB:EA:35   
          Bit Rate:36 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-63 dBm  Noise level=-96 dBm
          Rx invalid nwid:6928  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

---

### Post by Brightbelt on 2008-05-21
Hi, I don't know if you're on an intel or not. If not this post won't help you. But I configured my wireless on my Macbook Air with Ndiswrapper and I have had no problems. 

This link might give you some ideas anyways...
[https://help.ubuntu.com/community/Macbook_Air?highlight=%28Macbook%29%7C%28Air%29](https://help.ubuntu.com/community/Macbook_Air?highlight=%28Macbook%29%7C%28Air%29)

Sometimes the windows INF file (needed for Ndiswrapper) comes with your Boot Camp files in your system CDs you get at purchase. 

This is not to discount what you've tried already; madwifi and your code there are over my head...
(Also, IF you plan to try Ndiswrapper, I've heard it helps to uninstall Madwifi first.) 

I hope this helps, Frank B.

---

### Post by HuoMaKe on 2008-05-22
Turns out this is working a lot better than Madwifi. I ran it all last night (with a ping going to let me know if/when it quit out) and it only skipped about 10 times (probably because I moved the computer). This was never possible before.

Thanks, ndiswrapper!

Also Brightbelt. You helped a little, too.

---

### Post by russo.mic on 2008-05-22
> **Brightbelt said:**
> Hi, I don't know if you're on an intel or not. If not this post won't help you. But I configured my wireless on my Macbook Air with Ndiswrapper and I have had no problems. 

This link might give you some ideas anyways...
[https://help.ubuntu.com/community/Macbook_Air?highlight=%28Macbook%29%7C%28Air%29](https://help.ubuntu.com/community/Macbook_Air?highlight=%28Macbook%29%7C%28Air%29)

Sometimes the windows INF file (needed for Ndiswrapper) comes with your Boot Camp files in your system CDs you get at purchase. 

This is not to discount what you've tried already; madwifi and your code there are over my head...
(Also, IF you plan to try Ndiswrapper, I've heard it helps to uninstall Madwifi first.) 

I hope this helps, Frank B.

Just wanted to backup ndiswrapper as well, I have never had madwifi working nearly as well, although mine almost NEVER skips.  I have to say, it works equally as well in linux as it does in OS X or windows for me.

Russo

---

