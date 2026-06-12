---
title: "Bactrack 5r3 WIRELESS USB ADPTER PROBLEM!! pLZ HElp!! ;( im 3 weeks stock!"
date: 2014-06-19
forum: Any Other OS
---

### Post by ayan3 on 2014-06-19
root@bt:~# lsusb
Bus 002 Device 006: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 005: ID 0e0f:0007 VMware, Inc. 
Bus 002 Device 004: ID 0e0f:000a VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

==================================================

wlan0     Link encap:Ethernet  HWaddr 00:1a:ef:41:f7:ff  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

===================================================
root@bt:~# iwconfig
lo        no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

====================================================

airmon-ng


Interface    Chipset        Driver

====================================================

root@bt:~# ifconfig start wlan0
wlan0: Unknown host
ifconfig: `--help' gives usage information.

====================================================

HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz
HELP! plzzzzzzzzzzzzz

---

### Post by oldos2er on 2014-06-20
Moved to Other OS/Distro Support.

---

### Post by coffeecat on 2014-06-21
A couple of points:

1 - Backtrack has been unmaintained for a long while now and has been replaced by Kali Linux.

2 - We do not support airmon/aircrack here, which is why I have closed this thread.

And a piece of advice. You posted no fewer than 4 identical threads in different parts of the forum, which is a serious breach of forum etiquette both here and on other forums. If you decide to try Kali and need help on their forum, I suggest you read their forum rules first, which includes the same prohibition against cross/multiple posting as our rules do:

[https://forums.kali.org/showthread.php?8-Read-this-before-posting-%28Kali-Linux-forums-rules-and-guidelines%29](https://forums.kali.org/showthread.php?8-Read-this-before-posting-%28Kali-Linux-forums-rules-and-guidelines%29)

Thread closed.

---

