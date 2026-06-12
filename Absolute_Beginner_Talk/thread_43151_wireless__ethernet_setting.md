---
title: "wireless / ethernet setting"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by mysurface on 2005-06-20
When i was working i use wireless and when i was home i use LAN

i configure /etc/network/interface to put 

wireless on eth0
and lan on eth1

but it fails everytime i boot up and configure network is so slow.
what should i do?

/etc/network/interface
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
auto eth0

iface eth1 inet dhcp

auto eth1
```

---

### Post by benplaut on 2005-06-20
it might not be such a good idea to rename you Network Interfaces... best to leave ethernet to eth0, and wireless to either eth1, ath0, or wlan0 (changes depending on your card)

---

