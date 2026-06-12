---
title: "Need help with internet"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by ThirdGenLS1 on 2006-01-20
alright I just booted up ubuntu last night and i can't get it to connect to the internet if my life depended on it. I have a wireless card but for right now i'm just trying to get it working with my etho cord. When i plug the cord in it reads that i'm connnected but i just can't get any internet. Its in DHCP mode right now and when i enter in the ifconfig eth0 in the terminal i get

Link encap:Ethernet HWaddr 00:08:02: DO:35:58
inet6 addr: fe80::208:3558/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1355 errors:0 drpped:0 overruns:0 frame:0
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txpuenelen:100
RX bytes:62999 (61.5 KiB) TX bytes:2394 (2.3 KiB)
interrupt:11 Base adress:0xa800

and when i enter lspci | Eth
ethernet controller: Realtek Semiconductor Co., Ltd. Rtl-8139/8139c/8139C+ (rev 20)

When intering route -n it shows nothing in the gateway, genmask, ETC.

Any help would be greatly appreciated, cause i'm pretty excited to get this up and running.

---

### Post by wrtrdood on 2006-01-20
First assumption (since you mention eth0) is that you connect via Broadband.  What is your DHCP server?  It looks like you're not getting an IP address assigned.  Are you connecting directly or through a switch/router?  No IP can happen if you are connected to a router and it does not support DHCP.  Most ISPs these days provide DHCP so you might be able to test this by connecting directly to the modem.

The other thing to check is to log into your router (if that's possible) and use the utilities to turn on DHCP serving.  Otherwise you'll need to manually configure your IP address to match the Net address of the router.

---

