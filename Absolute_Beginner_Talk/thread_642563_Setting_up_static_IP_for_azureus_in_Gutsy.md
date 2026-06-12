---
title: "Setting up static IP for azureus in Gutsy"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Fungal Fractoids on 2007-12-16
I've tried searching on this but haven't been able to find an answer yet.

I connect to the net via a Linksys WRT54GP2 and am able to connect wirelessly no problems when in roaming mode, but whenever I try to assign myself a static IP I can't get a connection- not even to my router. Same happens with the wired connection. Which is strange becasue I had it working ok a few days ago before I reinstalled gutsy. The router has had  factory reset done since then too, but I am almost certain that there is no special configuration in the router to make this work properly.

My router dhcp assigns IP's between the ranges of 192.168.15.100-149

I've tried to configure my network settings as:

192.168.15.102
255.255.255.0
192.168.15.1.

In other topics like this people seem to ask for /etc/network/interfaces, so here goes it:

```
auto lo
iface lo inet loopback
```

Not a lot there, lol.

Can anybody see what I need to be doing here?

---

### Post by Fungal Fractoids on 2007-12-16
edit- double post

---

### Post by Fungal Fractoids on 2007-12-16
Should I try adding something like this to the end of /etc/network/interfaces?

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.15.102
netmask 255.255.255.0
gateway 192.168.15.1
dns-nameservers 192.168.15.1
```

If so, should the dns be my router, or should I put my isp's dns in there?

---

### Post by Fungal Fractoids on 2007-12-16
Eh, figured it out

:guitar:

Thanks to all who read ;)

---

### Post by AndyCooll on 2007-12-16
> **Fungal Fractoids said:**
> Eh, figured it out

:guitar:

Thanks to all who read ;)

For the benefit of others, how did you solve it?

:cool:

---

