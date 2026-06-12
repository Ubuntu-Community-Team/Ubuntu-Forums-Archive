---
title: "Internet Connection with 2 Network interfaces"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Andrea_44 on 2006-10-04
Hi,

I have two network interfaces (etho & eth1), both working properly.

eth0 is connected to another ubuntu PC.
eth1 is connected to a wireless lan for Internet.

The problem is I cannot connect to the Internet. Firefox return page not found for all websites, I cannot ping google etc. 

However, if I disconnect eth0(connected to a PC) and restart my machine, I am able use the Internet via eth1.

How configure my machine to use eth1 to connect to the Internet while eth0 is also connected to another PC.

Thank You,
Andrea

Following is my ifconfig:

eth0      Link encap:Ethernet  HWaddr 08:00:46:6A:0C:B0
          inet addr:169.254.4.217  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a00:46ff:fe6a:cb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8208 (8.0 KiB)  TX bytes:3006 (2.9 KiB)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:6D:C4:65
          inet addr:172.19.96.201  Bcast:172.19.97.255  Mask:255.255.254.0
          inet6 addr: fe80::202:2dff:fe6d:c465/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14369032 (13.7 MiB)  TX bytes:1486526 (1.4 MiB)
          Interrupt:9 Base address:0x3040

---

### Post by davmac on 2006-10-04
Andrea,

I've never tried to set up a machine with two network cards before so please take this with a pinch of salt!

I'd guess that it's a problem with defining the gateway - effectively telling your machine which route to use to get out. If you're using dynamic IP allocation then you need to know where your DHCP server is running and make sure that this is providing the relevant gateway IP address. If you're not sure about this you could try to convert your machine (temporarily) to use a staic IP address. I only suggest this because it's the only option I can think of to take this forward - I suspect there is a proper answer to insert at this point!

Select Systems > Administration > Networking. Then select ETH1 and Properties. On the connection settings choose a static IP address instead of DHCP and then fill the rest of the info in. Once you've clicked OK you may need to select the DNS tab and supply your DNS ip addresses. If you're not sure what they should be have a look at the file /etc/resolv.conf.

Hope this is of use,

Dave Mac

---

### Post by ssalman on 2006-10-05
had the same issue, see my last post in [this ]("http://www.ubuntuforums.org/showthread.php?t=255520")thread, hope it helps!

---

