---
title: "Shared directories?"
date: 2010-10-29
forum: Apple Hardware Users
---

### Post by NoBugs! on 2010-10-29
Anyone know why Mac OS computers show nearby mac shared directories, while Ubuntu won't show them on the places - network, or places - network - windows network? Is there a way to fix this? They're both on the same network...

---

### Post by NoBugs! on 2010-11-06
So is this impossible? Are they sharing with something like iTunes DAAP that can only be used with Apple devices?

---

### Post by blueridgedog on 2010-11-07
MacOSX uses a proprietary sharing service called Bonjour.  You can access it with Linux via the packages Avahi and nss-mdns.

You can read more about here (as well as Avahi):

[http://en.wikipedia.org/wiki/Zero_configuration_networking](http://en.wikipedia.org/wiki/Zero_configuration_networking)

---

### Post by NoBugs! on 2010-11-07
After installing those packages, it still won't connect. On the same computer, same network, rebooting to Mac OS shows all the shared directories in Finder under "shared", when clicked it shows "connected as guest" and the shared folders. According to [this]("http://developer.apple.com/opensource/"), Bonjour is an open-source protocol, but it doesn't say what program can use it on Linux.

---

