---
title: "Don't See Network Manager"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by mfmbcpman on 2006-11-24
I have Network Manager installed according to Synaptic but I don't see it anywhere. How do I access it?

---

### Post by PartisanEntity on 2006-11-24
In terminal type:

```
nm-applet
```

(Dont close the terminal, or it will close Network Manager. Or you can 'run' (alt+f2) it and you wont need the terminal)

to make it load at startup:

```
nm-applet --sm-disable
```

---

### Post by Marsolin on 2006-11-24
You should make sure to have either [KNetworkManager]("http://linuxappfinder.com/package/knetworkmanager") or [network-manager-gnome]("http://linuxappfinder.com/package/network-manager-gnome") installed.

---

