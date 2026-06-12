---
title: "Second NIC is registered but the link is not up"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-10-25
# dmesg |grep eth

eth0: registered as PCnet/PCI II 79C970A
eth1: registered as PCnet/PCI II 79C970A
eth0: link up
eth0: no IPv6 routers pressent

# cat /etc/network/interfaces

auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet static
  address 10.1.1.1
  netmask 255.255.255.0
  network 10.1.1.0
  broadcast 10.1.1.255
  gateway 10.1.1.254
  dns-nameservers 10.1.1.2
  dns-search domain.local

How should I go about troubleshooting why my second NIC's link is not 'up' (as in I don't see a eth1: link up in dmesg) at boot time?

Appreciate any help!


Thanks.

---

