---
title: "setting up a router"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by strahil on 2005-12-03
ok: I have my nic card working perfectly on the NET, but I want to plug my cable in a router(SMC7004VBR- ip: 192.168.2.1). Now what settings do I have to change to get it to work?

---

### Post by d1337 on 2005-12-03
If you have allowed Ubuntu to keep network interface seetings of dhcp, it should just work.  There's likely a simpler way if you are not familiar or comfortable with command line...quite possibly in network manager, but I've gotten so used to editing /etc/network/interfaces that I can do it blinded.  My file, with a router as 192.168.0.1 is as follows

```
/etc/network/interfaces
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
auto eth0
iface eth0 inet static
        address         192.168.0.137
        netmask         255.255.255.0
        network         192.168.0.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 151.164.1.8 151.164.64.201
```

but your settings may differ sllightly, especially your dns-nameservers as well as your network being 192.168.2.*

d1337

---

### Post by az on 2005-12-03
[QUOTE=strahil]ok: I have my nic card working perfectly on the NET, but I want to plug my cable in a router(SMC7004VBR- ip: 192.168.2.1). Now what settings do I have to change to get it to work?[/QUOTE]

You have to tell your router to connect to the internet in the same way your computer does .  Usually, the router can autodetect this while you run the setup wizard.

Your computer then connects to your router through dhcp.  If you tell the networking gui to use dhcp, it will get an address each time it connects.  By default, the networking GUI is set to static IP address, when most routers can use DHCP (as well as static, but DHCP is much simpler for you)

---

### Post by strahil on 2005-12-04
but do I have to run my router GUI first to allow the MAC adress of the card to use the NET(from my other pc:XP)?

---

### Post by d1337 on 2005-12-04
That likely depends on how you have your router secured.  Do you use MAC Address filtering?

d1337

---

