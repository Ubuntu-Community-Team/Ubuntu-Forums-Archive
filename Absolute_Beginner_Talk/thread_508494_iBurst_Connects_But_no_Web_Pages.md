---
title: "iBurst Connects But no Web Pages"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by arnold.pietersen on 2007-07-24
I am using a USB Iburst broadband modem for my Internet connection.  It seems that I am connecting, but I am not able to browse any web pages.  The following are some of the output:

arnold@arnold-laptop:~/Desktop/rp-pppoe-3.8$ sudo pppoe-start
. Connected!

arnold@arnold-laptop:~/Desktop/rp-pppoe-3.8$ sudo pppoe-status
pppoe-status: Link is up and running on interface ppp0
ppp0      Link encap:Point-to-Point Protocol          inet addr:196.2.103.149  P-t-P:196.2.100.1  Mask:255.255.255.255
         UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1392  Metric:1
         RX packets:3 errors:0 dropped:0 overruns:0 frame:0
         TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:3
         RX bytes:30 (30.0 b)  TX bytes:37 (37.0 b)

The TX bytes stays at 37 whereas the RX increase steadily.

Thanks

Arnold

---

