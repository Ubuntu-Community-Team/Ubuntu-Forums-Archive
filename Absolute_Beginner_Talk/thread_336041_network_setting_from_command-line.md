---
title: "network setting from command-line"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-01-11
I am having some troubles with X server, how can i setup the network settings (local ip, netmask, gateway, dns) from command-line?

Thanks

---

### Post by jvc26 on 2007-01-11
I think it would be:
```

sudo nano /etc/network/interfaces

```
The you can edit it like:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address *address here*
netmask *address here*
gateway *address here*

```

Il

---

### Post by hito1 on 2007-01-11
> **Illuvator said:**
> I think it would be:
```

sudo nano /etc/network/interfaces

```
The you can edit it like:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address *address here*
netmask *address here*
gateway *address here*

```

Il
What about DNS?

thank you.

---

