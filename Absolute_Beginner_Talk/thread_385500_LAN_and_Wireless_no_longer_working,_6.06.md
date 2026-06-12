---
title: "LAN and Wireless no longer working, 6.06"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by squig on 2007-03-15
My LAN shows up as eth0, wireless as eth1. Usually eth1 seems to never stop being the default gateway, when I try to change from the GUI. I can see that the LAN connection is receiving packets, but Firefox, Evolution, and KTorrent are not able to send or receive anything. 

I'm running a dual boot and am now accessing forum from XP :-(

I'm new to the command line, but very good at following instructions. Any help would be great.

Thanx,
Squig

---

### Post by banditti on 2007-03-15
Can you go to a command line and copy and paste the contents of

```
sudo gedit /etc/network/interfaces
```

---

### Post by squig on 2007-03-15
```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth1 inet dhcp

auto eth0
```

---

