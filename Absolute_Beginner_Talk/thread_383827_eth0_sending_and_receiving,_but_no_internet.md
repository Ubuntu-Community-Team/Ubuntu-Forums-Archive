---
title: "eth0 sending and receiving, but no internet"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by squig on 2007-03-13
Hello. I've seen lots of other posts that seem similar to this on the forums, but I don't know enough to decipher many of them, so I'm just going to post on my own. I apologize if I should have done better research.

I am running 6.06 as a dual boot with Win XP on a Dell Inspiron 9300.
I have an ethernet cable connected to the laptop. 
The problem is that when I deactivate the wireless connection, eth1, I have no internet in Firefox, and no Evolution email. 

When I look at the info for eth0, I can see that it is sending and receiving packets.

To get Internet and mail, I have to enable eth1. The wireless symbol (green bars) does not appear when I do this. 

I looked at an earlier forum which told user with a similar problem to run ifconfig and iwconfig. I will paste my results of those queries below.
```

amy@amy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:E9:1D:6B
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fee9:1d6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24676 (24.0 KiB)  TX bytes:1868 (1.8 KiB)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:13:CE:3F:5C:46
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe3f:5c46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1409 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:996609 (973.2 KiB)  TX bytes:176259 (172.1 KiB)
          Interrupt:201 Memory:dfcfd000-dfcfdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

amy@amy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:28:CE:F5
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/100  Signal level=-66 dBm  Noise level=-74 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:38

sit0      no wireless extensions.

amy@amy-laptop:~$

```

Many thanks for any assistance.

---

### Post by squig on 2007-03-13
Another note: every time I open the Network Settings GUI, it says that eth1 is the default gateway device. I have changed it many times in the GUI, but it does not change when I reopen.

---

### Post by jeffathehutt on 2007-03-13
I think that default gateway is the problem.  Are you connected to two different routers or just one?  (for instance, one wireless router and a seperate wired one).  Also, are you using DHCP to set up the network?

Run this command and post the output here, it could help diagnose your problem:
```
route
```

---

### Post by squig on 2007-03-13
Thank you, Jeffatthehutt. It turned out that I had both wireless and ethernet on at the same time--apparently this is a bad idea. I deactivated wireless and now the eth0 works fine. 

~A

---

