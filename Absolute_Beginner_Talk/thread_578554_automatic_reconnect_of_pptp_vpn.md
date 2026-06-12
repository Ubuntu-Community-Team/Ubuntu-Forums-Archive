---
title: "automatic reconnect of pptp vpn"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by bejurne on 2007-10-17
I am running the rc of Gutsy with all current updates installed. I use the pptp plugin of network manager to connect to a vpn network. This works perfectly. 

The problem is, that the vpn connection is not very stable. It breaks up regularly. I know that this is not due to the operating system since it happens in windows as well. My question is now, whether there is a way to automatically reconnect to the vpn, when the connection breaks up. Up till now I have to manually disconnect and then connect again to get it working. This gets kind of annoying if you have to do this every 15 min.

Thanks for the help
Bejurne

---

### Post by cmnorton on 2007-10-17
If you are going over wireless, you might have to reduce mtu to 1404 or lower.

---

### Post by bejurne on 2007-10-17
Wow, that was a quick response.

I am connected via cable to my dsl modem. I know the problem lies with the server i connect to, since others connecting to the same vpn have the same problem. So what I need is a way of Ubuntu realizing the connection is broken and then doing an automatic reconnect.

---

### Post by tro on 2007-11-25
Having the same issue. Bump.

---

### Post by chronos00 on 2008-02-07
I have the same problem. Is there any way to set automatic reconnection?

Maybe ping constantly the VPN server or some other ip that responds pinging like a router on the side of the LAN where the VPN server is.
I don't know much about scripting, but perhaps the autoreconnect can be achived with a custom script.

Other posibillity is to find a console configuration for vpn pptp connection.

Any ideas?

---

### Post by soulbreak on 2008-04-01
bump. same problem.

---

