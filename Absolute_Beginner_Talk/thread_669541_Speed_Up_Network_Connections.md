---
title: "Speed Up Network Connections"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-01-16
Dell D820
Gutsy 7.10

Now that I finally have my bcm43xx-firmware installed and running. Is there anyway to speed up my connection? The connection is rated at 24 Mb/s but I am luck to get 505 B/s. Also here on campus we have gigabyte service to the desktop and my wired connection isn't even coming close. Is there anywhere I can tune up my connections? Thanks!

---

### Post by morgan_greywolf on 2008-01-16
Try this:

```
$ sudo ethtool eth0
```

(or substitute whatever your broadcom adapter is called).

You should output that looks something like this:

```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: yes

```

The part you care about are 'Speed' and 'Duplex'.  By your symptoms, I'd say yours probably says something like "10Mb/s" for "Half" for duplex, or something equally unuseful.  That usually indicates a problem with autonegotiation between your NIC and the switch.  Some older Cisco GigE switches are notorious for this, especially if not configured properly.

If that's the case, try turning autonegotiation off with something like this:

```
sudo ethtool -s eth0 speed 1000 duplex full autoneg off
```

HTH

---

### Post by k8fox1 on 2008-01-16
Ok tried it and got the following:

Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg


Also what can I do to speed up the wireless?

Thanks!

---

### Post by morgan_greywolf on 2008-01-16
The **sudo **part is very imjportant.

```

sudo ethtool -s eth0 speed 1000 duplex full autoneg off
```

---

### Post by k8fox1 on 2008-01-16
Still getting:

mdt2@mdt2-ubuntu-laptop:~$ sudo ethtool -s eth0 speed 1000 duplex full autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg
mdt2@mdt2-ubuntu-laptop:~$

---

### Post by morgan_greywolf on 2008-01-17
Your adapter must not be called 'eth0'.

What's the output of:

```
ipaddr
```

---

### Post by k8fox1 on 2008-01-17
Ahh this morning I tried againg and got back:

----

mdt2@mdt2-ubuntu-laptop:~$ sudo ethtool -s eth0 speed 1000 duplex full autoneg off
[sudo] password for mdt2:

----


Since we're back to the prompt I assume I'm good?

Also, is there anything I can do to speed up my wireless connection?

Thanks!!

---

### Post by kvonb on 2008-01-17
_-_

---

### Post by k8fox1 on 2008-01-18
Thanks!

---

