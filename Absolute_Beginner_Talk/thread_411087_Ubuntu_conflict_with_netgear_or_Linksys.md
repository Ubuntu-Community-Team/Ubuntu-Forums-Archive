---
title: "Ubuntu conflict with netgear or Linksys?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-04-16
In the past two days (when i started using ubuntu as my primary operating system) my house started to have network problems.  The internet would be inconsistent and we would have to reboot the Linksys Router and netgear 12 port switch.  Ive had some problems as well, but as  of this moment no computer in my house running windows xp can connect to the internet while I can.  Im wondering if maybe my network settings on ubuntu could be crashing either the switch or router?

Once again I have to thank all of you for the help.  If it wasnt for this forum I wouldnt be using Ubuntu ;) You are all very kind and more then willing to put up with my noobish questions.  Thanks.

---

### Post by caffienefree on 2007-04-16
I highly, highly doubt that's the case, but you can experiment a little. With your ubuntu computer turned off, can the XP computers access the internet?

---

### Post by dreadh3ad on 2007-04-16
fixed the problem.  I was using DHCP, when i gave my computer a static IP address all problems ceased.

---

### Post by kahrytan on 2007-04-16
Routers can crash when they reach their limit for connections. Are you downloading from Bittorrent allot? All those multiple connections could cause a crash and require a hard reboot of the router. I know because my router has same problem occassionally.

---

### Post by dreadh3ad on 2007-04-16
I was running 2 bit torrent downloads + multiple tabs in firefox + aim.  Apparently our network is still crashing for xp users but i havent had any trouble....

Im out of ideas for the moment

---

### Post by n3tfury on 2007-04-16
> **dreadh3ad said:**
> I was running 2 bit torrent downloads + multiple tabs in firefox + aim.  Apparently our network is still crashing for xp users but i havent had any trouble....

Im out of ideas for the moment

i don't understand how a network can "crash" for XP users and not you.  if your bit torrent client is still running, exit the application and power cycle the router.

---

### Post by kahrytan on 2007-04-16
> **dreadh3ad said:**
> I was running 2 bit torrent downloads + multiple tabs in firefox + aim.  Apparently our network is still crashing for xp users but i havent had any trouble....

Im out of ideas for the moment



Then thats your problem. Bit torrent. Bit torrent crashes even Zone Alarm on Windows.

Routers can handle only around 250 connections. I had the same problem and did some Google research. Try using a client that can limit connections.

---

### Post by nautilus on 2007-04-16
if you have one or more computers using dhcp, and one or more using static addressing, you inherently have a problem.

bad things happen when a router assigns an IP to a computer while the IP is already in use, I suggest you decide on one or the other, and/or if you must mix them, use static addresses which your router will route, but not hand out via DHCP.  most routers can do this, if you fiddle in their cheezy webconfig for a bit.

---

### Post by dreadh3ad on 2007-04-16
Well i know linux isnt the problem.  Ive had my system offline for nearly and hour and the internet keeps crashing.  Although when i plug my computer back in im the only one who can get internet.  Weird.

---

### Post by zoogTHOMzoog on 2007-04-16
I run several different OS's(Ubuntu, Debian Etch, Zenwalk 4.*, MS XP, MS VISTA, OpenSuSE, and FreeBSD) on my router (netgear wireless bg) without any problems. However, when I was using static routes, the router occasionally had issues with two different IP's being assigned to the same mac address (where the host-names were different, e.g. "ubuntu-hostname", XP "hostname"). Now I run everything with DCHP. As Nautilus suggested, if you are using static routes and dynamic routes make sure you have it set up (usually under advanced settings in your router's config page) so that your router does not assign the same IP more than once.

Cheers and good luck!
~Thom

:guitar:

---

