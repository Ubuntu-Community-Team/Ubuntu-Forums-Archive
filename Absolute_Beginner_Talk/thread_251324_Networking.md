---
title: "Networking?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Haggis on 2006-09-05
I am trying to connect to my local network and am struggling to get it to work in Ubuntu.  My local network administrators only provide support for Windows.

As per the Ubuntu documentation, I went to System->Networking and activated my Ethernet connection.  I then set my IP address setting to DHCP as instructed by the network (this worked under Windows).  After doing this I could access local hosts.

In Firefox, I set my proxy settings to the automatic proxy configuration URL also as instructed.  I was then unable to access any pages - local or otherwise.  I could no longer ping within the network either.  I changed this setting back (to direct connection) and was still unable to ping within the network.

Under network tools it says I am receiving bits, but not transmitting.

What else do I need to set up?

---

### Post by jorn on 2006-09-05
I'm not saying that I'm able to help you.
To see all your connections please paste the output of:
> ifconfig

---

### Post by Haggis on 2006-09-05
The output of ifconfig is:

eth0   Link encap: Ethernet HWaddr 00:80:AD:73:EF:B3
       inet addr:172.16.112.192  Bcast:172.16.115.255  
       Mask:255.255.252.0
       UP BROADCAST MULTICAST  MTU:1500  Metric:1
       RX packets:3095 errors:190 dropped:0 overruns:0 frame:0
       TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:565476 (552.2 KiB)  TX bytes:2998 (2.9 KiB)
       Interrupt:9 Base address:0xd800

There is also output from lo underneath (loopback interface)

Thanks

---

### Post by Haggis on 2006-09-05
Fixed it using the thread below:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

Thanks!

---

