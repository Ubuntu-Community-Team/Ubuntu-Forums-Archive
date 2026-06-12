---
title: "NIC toggles on reboot - Help!"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Amplidude on 2007-07-17
My second NIC (eth1) is renamed (to eth2) after a reboot, crashing the network. If I reboot again it is seen as eth1 again, and the network works again. And so on.  Each time I reboot the NIC toggles between eth1 and eth2. I have no idea what is causing this but it's driving me nuts. Can anyone help please? I have no ideas. Thanks

My set-up of etc/network/interfaces is:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

