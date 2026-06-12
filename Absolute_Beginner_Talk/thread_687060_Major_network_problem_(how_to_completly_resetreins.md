---
title: "Major network problem (how to completly reset/reinstall networking)"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2008-02-03
I have been using the same Ubuntu box for about a year now. In fact, I have 4 of them in my house - all of them the exact same with the exact same hardware.

All has been fine, until I have been trying to upgrade my network. Something on one of the computers has changed. Here is the scenario:

For the last year, my network went like this:

DSL Modem (192.168.254.xxx) -> Belkin WirelessG Router (192.168.2.xxx) ->PCs

Everything has worked great.. However, now I am trying to change the network with a server with 2 NIC cards separating my internal network from the WAN. The server has DHCP services running on it. So the new setup will be:
DSL Modem -> Server WAN Nic / Server LAN Nic -> Gigabit switch -> PC's

The problem is, when I plug this one computer into the gigabit switch, it does not "sense" the DHCP serverand the network shows as disconnected, no matter what I try.
All other computers got assigned an IP address almost instantly upon plugging into the switch. Even this computer, when booted into windows graps an IP address from the DHCP on the server with no problem. This shows that the DHCP services are running correctly on the core, and also shows that the NIC and wiring is good (as windows connects with no problem on the same PC)

I have spent 3 days on this - the most important PC to get onto the new network is the one that doesn't work (go figure)


What can I check for? How can a reinstall and/or reset to defaul;ts the networking portion of Ubuntu? Can anyone help?

thanks,

Jon

---

### Post by bettlebrox on 2008-02-03
>The problem is, when I plug this one computer into the gigabit switch, it does not "sense" the DHCP serverand the network shows as disconnected, no matter what I try.

It is running Ubuntu? What's in your /etc/network/interfaces file?

---

### Post by jondecker76 on 2008-02-04
Yes, it is Ubuntu 7.10


/etc/network has interfaces and also an interfaces.bak-0 file.

interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp



```


interfaces.bak-0:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


#iface eth0 inet dhcp



iface eth1 inet dhcp

auto eth1





iface eth0 inet dhcp

auto eth0


```



though I have tried both to no avail...

---

