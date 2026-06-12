---
title: "ndiswrapper getting bit rates = failure"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by mikesty on 2006-08-03
Xubuntu Dapper.

I completely gave up trying to use the linux drivers, so I went with NDISWRAPPER. This is the second time I'm using it. I went into synaptic and got ndiswrapper, the sources if needed, and the ndisgtk doodad to make things a little easier.

Pop in the CD for the Zonet ZEW2501 using zd1211b chipset, grab the WinXP INF and everything is cool. I reboot, it now takes a minute or two to discover network devices. I get to the desktop, Network Manager doodad won't load at all. Wlan0 does exist and dmesg shows it exists too, but dmesg keeps giving the following errors numerous times:

```
ndiswrapper (iw_get_range:1415): getting bit rates failed 
```

What???

OK, the network manager finally came up. Wlan0 was active already so I double cheked the settings and then just deactivated eth0.

Dmesg then says:

```
wlan0 No IPv6 routers present
```

Well duh, only using IPv4. Is that the source of my troubles? Thanks.

---

### Post by mikesty on 2006-08-03
Maybe the problem is inside /etc/network/interfaces ???

---

