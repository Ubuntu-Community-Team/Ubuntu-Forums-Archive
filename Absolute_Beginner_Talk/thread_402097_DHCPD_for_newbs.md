---
title: "DHCPD for newbs"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Pontiac on 2007-04-05
I've been playing with Ubuntu for a few months now, and have been enjoying myself a LOT since Edgy has been released.  Any other flavour of linux has driven me absolutely insane (including that of Ubuntu) and within hours I managed to get panics out of the kernel.  Quite a feat, I would say. ;)

I won a victory today, so I thought I might share it with my fellow beginners.

I am the only technician in a computer shop.  I work on sick computers for a living.  Literally around a thousand machines come across my bench each year.  I've seen my share of annoyances, and "Why the f..... isn't this doing what I want it to do?".  I've learned a LOT about the internals of Windows and where to find them nasty lil' critters we call viruses and spyware.  My ratio of REFORMAT:RECOVER is pretty darned close to zero. ;)  This linux box is also the only linux box out of 8 machines.  The other 7 are Windows based.  Every customer machine thats been on my bench has also been Windows based.  Everything from Win3.1 to Win XP.  No Vista for me yet (Fortunately)

ANYWAYS... A victory for me against DHCPD3.

I use two machines.  One is named RedDawg (WinXP Pro box) and Radius (The linux box) We must have lost electricity over night, cuz I found RedDawg had been restarted, the and Radius was sitting at the login screen.  I also noticed that the three shares I have pointed at Radius from RedDawg were not working properly.

I went into a shell and did the following
```

root@radius:/etc/init.d# ./dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail]
 * Starting DHCP server dhcpd3                                           [fail]

```

Both failed.

Yet
```

root@radius:/etc/init.d# dhcpd3 eth2
Internet Systems Consortium DHCP Server V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Wrote 0 deleted host decls to leases file.
Wrote 0 new dynamic host decls to leases file.
Wrote 1 leases to leases file.
Listening on LPF/eth2/00:18:e7:08:bc:7a/10.1.1/24
Sending on   LPF/eth2/00:18:e7:08:bc:7a/10.1.1/24
Sending on   Socket/fallback/fallback-net

```

So theres gotta be a conflict somewhere as to which server is listening to what device.  As of this writing, I DON'T know if I'm running two DHCP servers on the same card.  Oh well.  Som'n breaks I'll know about it. ;)

I have been using Webmin 1.330 for most of my configuring of certain services as my intimate knowledge of linux is still pretty darned close to my REFORMAT:RECOVER ratio. ;)  Not sure if I found a bug, but for whatever reason WebMin wasn't changing what ethernet card it was supposed to listen to DHCP requests.

So to the prompt I go.  From past experience, I know that /etc/init.d/ is the directory where services are started/stopped/restarted.  I know that they're all scripts in there as well.  So I looked for all files via ls that are named dhcp.  I found dhcp3-server.  I used pico on it to find out how the script runs.  I found out that a config file lives in /etc/default/ called dhcp3-server.  I opened up another shell, and ran pico to edit the file, and sure enough it was pointed to eth1 (Which for some reason existed prior to the forced reboot).  I changed the file to point to eth2.  Wrote the file, and restarted the server, and voila, it worked.

```

root@radius:/etc/default# /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail]
 * Starting DHCP server dhcpd3                                           [ ok ]

```

I would suggest that if you have an issue trying to get a particular service installed, and having it operate in a certain way, yes webmin is a good method to get it going, but, don't rely COMPLETELY on it.  Read whats in init.d and enjoy. :)

---

### Post by chalex on 2007-04-06
Just take a look at /etc/dhcpd.conf

or "man dhcpd.conf"

---

### Post by Pontiac on 2007-04-09
Reading through the dhcpd.conf file, theres no mention anywhere as to what ethernet port the daemon is supposed to listen to, which was causing most of my issues.  MOST of the time, MOST people have just one ethernet card in their machine.  This particular machine sits on two networks, one with a DHCP server on it, the other without.  WebMin gave me the option to select which ethernet port it works on, but wouldn't actually SET the option, which caused me to dig deeper.

---

