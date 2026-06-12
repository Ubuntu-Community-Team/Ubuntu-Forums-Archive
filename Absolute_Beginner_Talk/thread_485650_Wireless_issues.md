---
title: "Wireless issues"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by MotleyPhule on 2007-06-27
Hi,

I'm a total beginner to Ubuntu.  I've installed Feisty Fawn it as a dual boot thing, and it seems to work great.  It detects all the hardware, including my wireless network card.  However, I was having problems getting it to connect to the network.  I have no WEP running since I live in a rural spot.  After searching through forums and playing with different things, I've found that it works if I manually configure it to be a local zeroconf network, and if I then open a terminal and enter these mystical phrases:

$ sudo dhclient ra1

followed by 

$ sudo lshw -C network

After that it's stays connected until I reboot!

If anyone knows what I can do to resolve a more permanent solution or even let me know what the hell it is I AM doing, then it would be much appreciated.

Regards,
Richard

---

### Post by Austin_KW on 2007-06-27
The "$ sudo dhclient ra1"  will run a dhcp client on interface ra1. This will get an ip address, default gateway and dns server from your router. If the interface is not up dhclient will first bring up the interface and associate with your wireless router.

The lshw only lists your network hardware, has no effect in setting configuration

To automatically do the configuration on boot modify your /etc/network/interfaces with
gksudo gedit /etc/network/interfaces   (from a terminal)
and add/modify the following lines for ra1
```

auto ra1
iface ra1 inet dhcp

```

---

