---
title: "ubuntu / wifi problem, on a macbook pro"
date: 2019-12-08
forum: Apple Hardware Users
---

### Post by fredy50 on 2019-12-08
Some time the wifi will disconnect and i need to reboot my computer.
When i reboot i can connect to wifi, but it happens again and again.

Hardware:
macbook pro

Software:
Ubuntu 16.04

-----------------

Comamnd: nmcli g
STATE         CONNECTIVITY  WIFI-HW   WIFI      WWAN-HW  WWAN    
disconnected  none          disabled  disabled  enabled  enabled

Another command: sudo rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

-----------------

How can i fix the issue?

---

### Post by uRock on 2019-12-08
Moved to ***"Apple Hardware Users"*** sub-forum for better visibility.

---

