---
title: "Network manager crashes after 15 mins"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2007-10-09
Dear everyone
I have recently been experiencing a lot of network disruptions in my ubuntu fiesty fawn 7.04. After about 15 mins from boot time, my network manager crashes and that leaves my computer unable to connect to the internet. I have found a temp solution to this:

1) I end process NetworkManager, NetworkManagerDispatcher and nm-applet
2) Manually pull out my cable,
3) restart and then plug in the cable.

I do not understand how my network manager can just "crash". What files should i post to discuss a possible diagnostics for my problem? 
What should i do?

---

### Post by disappearedng on 2007-10-09
For the record, this is how my /etc/network/interfaces look like:

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

which is NOT the normal format.

Is this "wrong?"

---

