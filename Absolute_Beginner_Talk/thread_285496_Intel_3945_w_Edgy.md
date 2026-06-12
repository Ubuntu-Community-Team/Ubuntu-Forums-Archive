---
title: "Intel 3945 w/ Edgy?"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Lysander on 2006-10-26
Hey all,

I have just completed a fresh install of Edgy, and have a problem. I have an Intel 3945a/b/g wireless card, under Dapper with network-manager, it was perfect. However, under Edgy, with network-manager, the taskbar applet doesn't even list my wireless card. 

Here is a sample of my iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3395   Missed beacon:0

sit0      no wireless extensions.

```

I tried using wifi-radar instead, and it would pick up my AP, but would not connect to it. My AP is just using a standard password to allow access. 

Any help getting this working would really be appreciated, as I would love to try out Edgy.

Lachlan Cannard

---

### Post by Lysander on 2006-10-26
Never mind, I fixed my own problem. I merely commented out all the devices in my /etc/network/interfaces file, except for the loopback. I restarted and voila!

---

### Post by ljk25 on 2006-11-24
thanks, u make my day. got the same problem. will try it out.

---

