---
title: "Wiress issues b43"
date: 2013-04-16
forum: Any Other OS
---

### Post by blazer73 on 2013-04-16
Ok so I have dual booted my system on Linux Mint Mate 14 I have all my wireless drivers working. My second OS on a seperate hard drive I have Pear OS 7 wireless set up exactly the same. Grub is able to see both OS. However when I try to connect to the wireless it trys to connect and then comes back with authenitication failure. I have searched google and tried several different options. I reset the router and tried all ways that I found suggested. The card is a Netgear Broadcome 4321 any ideas?

ip link show returns:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT qlen 1000 link/ether c8:60:00:6b:52:83 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT qlen 1000 link/ether 2c:b0:5d:1f:08:4c brd ff:ff:ff:ff:ff:ff

this is what shows on my linux mint os that the wireless is working on the same machine. 

ip link show returns:


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN mode DEFAULT link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT qlen 1000 link/ether c8:60:00:6b:52:83 brd ff:ff:ff:ff:ff:ff 
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT qlen 1000 link/ether 2c:b0:5d:1f:08:4c brd ff:ff:ff:ff:ff:ff 

this is what was returned from the OS that is not connecting to wireless.

---

### Post by Perfect Storm on 2013-04-16
Moved to Other OS/Distro Support.

---

