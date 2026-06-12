---
title: "problem in enabling monitor mode in  Broadcom Corporation BCM4312 wireless driver"
date: 2011-10-13
forum: Any Other OS
---

### Post by aditya anand on 2011-10-13
i have installed linux mint 10 gnome. my wireless run on interface eth1.
i installed aircrack-ng and try to activate monitor mode on throug airmon-ng . but it fails..


 aditya aditya # airmon-ng

Interface     Chipset           Driver

eth1                Unknown            wl

aditya aditya # airmon-ng start eth1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
934    avahi-daemon
935    avahi-daemon
1018    NetworkManager
1061    wpa_supplicant
4021    dhclient
Process with PID 4021 (dhclient) is running on interface eth1


Interface      Chipset          Driver

eth1                 Unknown                  wl (monitor mode enabled)

my wirless card is 
Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by bkratz on 2011-10-13
sorry, but the STA driver (listed as wl) is the official Broadcom driver and does not support aircrack or going into the mode you are trying to do.

---

### Post by Perfect Storm on 2011-10-13
Moved to Other OS/Distro Talk.

---

### Post by daniel.p on 2011-10-14
> **aditya anand said:**
> i have installed linux mint 10 gnome. my wireless run on interface eth1.
i installed aircrack-ng and try to activate monitor mode on throug airmon-ng . but it fails..


 aditya aditya # airmon-ng

Interface     Chipset           Driver

eth1                Unknown            wl

aditya aditya # airmon-ng start eth1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
934    avahi-daemon
935    avahi-daemon
1018    NetworkManager
1061    wpa_supplicant
4021    dhclient
Process with PID 4021 (dhclient) is running on interface eth1


Interface      Chipset          Driver

eth1                 Unknown                  wl (monitor mode enabled)

my wirless card is 
Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

You'll have to use the b43 driver, not the STA driver in order to have the card function properly with what you're trying to do. What kernel are you using? It took me awhile to get my wireless up and running with that same card and the b43 driver - it had to do with a kernel issue. After trying out 4 other kernels I was up and running.

---

### Post by linuxaddix on 2011-10-16
find gerix wifi cracker for your linux

---

