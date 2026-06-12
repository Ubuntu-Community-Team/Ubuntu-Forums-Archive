---
title: "[XUBUNTU] DHCP favors wireless (!)."
date: 2007-05-11
forum: Apple Intel Users
---

### Post by phibxr on 2007-05-11
I've tried installing both Ubuntu and Xubuntu, and while Ubuntu does a great job configuring my network with DHCP via eth0, Xubuntu (for some strange reason) does not. Instead it finds an open access point somewhere in my house (a quite large block of flats, so I don't have a clue who owns it) and uses it by default, even if I do:

```
ifconfig ath0 down
dhcpcd eth0
```

My model specifications is as follows (the names are in Swedish, since I'm currently running OS X in Swedish, but you shouldn't have any problems following them anyway :).

```
 Maskinens namn:	Mac mini
  Datormodell:	Macmini1,1
  Processornamn:	Intel Core Duo
  Processorhastighet:	1.83 GHz
 Typ av kort för trådlös anslutning:	AirPort Extreme  (0x168C, 0x86)
  Miljö trådlöst kort:	Globalt
  Fast programvaruversion trådlöst kort:	0.1.27
```

By the way, I think it's great that 7.04 supports AirPort Extreme out of the box. Just too bad that I don't need it. ;)

---

