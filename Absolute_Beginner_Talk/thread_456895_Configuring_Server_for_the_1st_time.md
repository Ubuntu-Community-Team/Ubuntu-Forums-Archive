---
title: "Configuring Server for the 1st time"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by fulanitok on 2007-05-28
Hi Guyos,

I trying to configure my Ubuntu Server for the first time, I wanna to host the online games of my Clan!

When I check: sudo vi /etc/network/interfaces 

I get this: 

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0

What am I doing wrong?

---

### Post by Carlos Santiago on 2007-05-28
What do you want to do?
Setup a private LAN?

Place the answer of the command ifconfig

---

