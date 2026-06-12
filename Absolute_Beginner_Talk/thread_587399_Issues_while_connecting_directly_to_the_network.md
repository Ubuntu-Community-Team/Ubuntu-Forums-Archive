---
title: "Issues while connecting directly to the network"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-10-22
Today our server collapsed and i had to connect to the internet acting as a server. The problem is, when i configure Ubuntu with the public ip (gateway and dns included) i cant connect to the internet. I could through the server, using 100 mbps with autonegotiation. I tried to force my network card to 10 mbps (thats the speed my isp works with) using mii-tool and ethtool but none of this worked.

Here is my /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 190.15.199.211
netmask 255.255.255.0
gateway 190.15.199.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

I tried forcing 10 mbps HD and FD with mii-tool and ethtool, but still no results. Is there anything im doing wrong?

---

### Post by ferpadro on 2007-10-22
anyone?

---

