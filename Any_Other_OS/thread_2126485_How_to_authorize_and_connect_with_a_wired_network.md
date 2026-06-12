---
title: "How to authorize and connect with a wired network?"
date: 2013-03-17
forum: Any Other OS
---

### Post by Houmie on 2013-03-17
Hi,

I have a satellite internet provider that requires username/password for a wired connection.

I can set this connection up successfully under windows but I fail doing it so in Linux.

[ATTACH=CONFIG]240279[/ATTACH]
Under Windows I setup a PPPoE connection and username and password and it works.

In Linux Mint 14 (based on Ubuntu 12.10) when I activate 802.1X authentication and use MD5, it doesn't succeed.  Could it be that I need a PAP authentication type instead of MD5? 

Many thanks for your advice,
Hooman

---

### Post by sanderj on 2013-03-17
Wait: do you need PPPoE? If so, use that. Not 802.1X authentication.

Did you run pppoeconf ?

---

### Post by Houmie on 2013-03-18
Yes, you are right. After a lot of research I figured out what I need is PPPoE. Indeed pppeconf actually works fine.  However I fail at the next step, that is running pppoe connection over a VPN connection. (I have a VPN that works under Windows, with host, username and password) but don't know how to do it under Linux.

I am right now in a country that censors Internet, so the only chance to access data is through a VPN.

I have been told nowadays a lot of people just use network-manager with PPTP plugin to combine DSL and VPN.
I am been tinkering around with that (without using pppoeconf). I can add a new DSL connection, but I can't connect with it. There is no right click connect or anything.

---

### Post by Perfect Storm on 2013-03-18
Thread moved  to Other OS/Distro Talk.

---

