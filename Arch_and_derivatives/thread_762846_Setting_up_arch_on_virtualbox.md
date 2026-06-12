---
title: "Setting up arch on virtualbox"
date: 2008-04-22
forum: Arch and derivatives
---

### Post by shifty2 on 2008-04-22
I'm having issues setting up the network on arch - installed on virtualbox in windows. 

I think I have set it up correct, following the instructions on the wiki, but since ping doesn't work within virtualbox i have no way of testing if it works or not. When I try to update, I get this error posted in terminal:
```
Failed to synchronize core: Transient resolver failure
```
which I assume means I don't have a working internet connection.

Posting relevant bits:
network bit of rc.conf:
```
Hostname = "arch"
eth0="eth0 192.168.0.2 netmask 255.55.255.0 broadcast 192.168.0.255"
INTERFACES = (eth0)
gateway = "default gw 192.168.0.1"
ROUTES = (gateway)

```
resolv.conf:
```
nameserver 192.168.0.1
```

Could be missing something blindingly obvious here...but im a bit stuck to be honest. any help would be much appreciated.

---

### Post by fwojciec on 2008-04-22
> **shifty2 said:**
> I'm having issues setting up the network on arch - installed on virtualbox in windows. 

I think I have set it up correct, following the instructions on the wiki, but since ping doesn't work within virtualbox i have no way of testing if it works or not. When I try to update, I get this error posted in terminal:
```
Failed to synchronize core: Transient resolver failure
```
which I assume means I don't have a working internet connection.

Posting relevant bits:
network bit of rc.conf:
```
Hostname = "arch"
eth0="eth0 192.168.0.2 netmask 255.55.255.0 broadcast 192.168.0.255"
INTERFACES = (eth0)
gateway = "default gw 192.168.0.1"
ROUTES = (gateway)

```
resolv.conf:
```
nameserver 192.168.0.1
```

Could be missing something blindingly obvious here...but im a bit stuck to be honest. any help would be much appreciated.

If you're setting up Arch within the Virtualbox I'd go for the most generic dhcp setup possible:

```
Hostname = "arch"
eth0="dhcp"
INTERFACES = (eth0)
gateway = "default gw 192.168.0.1"
ROUTES = (!gateway)

```

Note the exclamation mark before the "gateway" in the ROUTES line.  Something like this should work, I think.

---

### Post by shifty2 on 2008-04-22
Ok got it working...think it was a "dhcpd eth0" command thrown in somewhere that made it burst into life.

Then got myself into a mess with the mirrors removing a "/" by mistake from one of the ftp:// bits. all sorted now though :-) thanks for the help

---

