---
title: "Getting only half internet speed over wireless using Katya (Linux Mint 11)"
date: 2011-08-08
forum: Any Other OS
---

### Post by X-jo on 2011-08-08
Hi, 

I have Linux Mint 11 Katya on my machine and I am getting  just half the speed(~300kbps) over wireless. I have a space machine  which has crunchbang on it and its gettiing full speed (~600kbps) over  wireless.

Any idea why?

Details of Katya Machine which is giving me less than half speeds

$ inxi -N
```
Network:   Card-1 Atheros AR9285 Wireless Network Adapter (PCI-Express) driver ath9k BusID: 02:00.0
           Card-2 Atheros AR8152 v2.0 Fast Ethernet driver atl1c v: 1.0.1.0-NAPI at port 2000 BusID: 01:00.0
```$ lsusb
```
Bus 002 Device 007: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 002 Device 003: ID 0930:0215 Toshiba Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 10f1:1a34  
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```$ lspci -nn | grep 'Wireless'
```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```Thanks

---

### Post by X-jo on 2011-08-08
Got it solved using [http://forums.linuxmint.com/viewtopic.php?f=90&t=78512&p=457605&hilit=wireless+backports#p457605](http://forums.linuxmint.com/viewtopic.php?f=90&t=78512&p=457605&hilit=wireless+backports#p457605)

---

### Post by Perfect Storm on 2011-08-09
Moved to Other OS/Distro Talk.

---

