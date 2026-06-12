---
title: "Multiple IP`s on different VLANs"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Bateau on 2008-01-21
hey!
i need to add another IP address to my server.
i allready have 2 IPs set up on this box, and they are both in different VLANs (VLAN1 and VLAN2).
the thing i am going to do now, is to add another IP in VLAN2...
how do i go about doing this?

---

### Post by blueridgedog on 2008-01-21
In /etc/network/interfaces you have something like:

```
iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1
```

You will add sections for virtual interfaces:
```

iface eth0:1 inet static
address 192.168.2.102
netmask 255.255.255.0
gateway 192.168.2.1

iface eth0:2 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
```

---

