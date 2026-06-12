---
title: "How to connect to internet?"
date: 2013-04-12
forum: Any Other OS
---

### Post by zt33 on 2013-04-12
Hi, i've installed Debian Squeeze yesterday, but i can't have acess to internet, neither to any interface to connect it (i'm on wireless).

At the installation it give an error saying that dhcp didn't worked out or something so i choosed "configure it later"... but it detected the network adapter (Atheros AR5001).

i've been searching, but i'm a noob on this, though, if i enter the "lspci |grep Network" command i receive "02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)" so i assume that the adapter is working but i can't have acess to internet.

Any help?

---

### Post by fr2632 on 2013-04-12
> **zt33 said:**
> Hi, i've installed Debian Squeeze yesterday, but i can't have acess to internet, neither to any interface to connect it (i'm on wireless).

At the installation it give an error saying that dhcp didn't worked out or something so i choosed "configure it later"... but it detected the network adapter (Atheros AR5001).

i've been searching, but i'm a noob on this, though, if i enter the "lspci |grep Network" command i receive "02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)" so i assume that the adapter is working but i can't have acess to internet.

Any help?

[COLOR=#000000][SIZE=2][FONT=arial]Can you ping? Have you checked into your network manager? What do you have in /etc/network/interfaces?

Please post:

```
ping www.google.com
``` 

and

```
cat /etc/network/interfaces
```[/FONT][/SIZE][/COLOR]

---

### Post by UltimateCat on 2013-04-13
Hi:

When I first installed Debian I couldn't connect to the internet either and I'm wireless too-

I had to go into this file too-
> /etc/network/interfaces


In my case Wired and Wireless where both indicated
I had to comment out the Wired argument with the (#) sign and when I re-started I had a wireless connection.

You can use Nano or Gedit to edit that file if you need to edit it-

---

### Post by Redalien0304 on 2013-04-13
have you tried sudo dhclient eth0.  works on live cd/usb at least for me.

---

