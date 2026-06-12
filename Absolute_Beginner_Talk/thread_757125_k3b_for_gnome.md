---
title: "k3b for gnome?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-04-16
can k3b be used with gnome in Ubuntu 7.10?  thanks.

---

### Post by Crafty Kisses on 2008-04-16
Yes, ```
sudo apt-get install k3b
```

---

### Post by Matt26 on 2008-04-16
i noticed the version in synaptics package manger is 1.0.3 but the latest version on the official website is 1.0.4- which version does the apt-get command download and install?  can the latest version from the website be downloaded and installed instead of using the command?

---

### Post by PeterJS on 2008-04-16
Synaptic is just a very pretty front end to libapt, much like apt-get is a very ugly front end to lib apt. They both draw from the same repositories. You can certainly get an upstream release of k3b, having to compile it yourself would be a pain in the backside hopefully they, or some kind third party, have released 1.04 in .deb format. You might look at what's in the hardy repos as well and wait a couple days (8) for the newest version to be included.

---

### Post by stchman on 2008-04-16
> **Matt26 said:**
> can k3b be used with gnome in Ubuntu 7.10?  thanks.

Of course, I use many KDE apps under Gnome.

K3b
K9Copy
KTorrent
Gwenview

They run well.  Only thing is that you need to load the KDE libraries.  I recommend you do that at start up.

[http://www.stchman.com/kde_fast.html](http://www.stchman.com/kde_fast.html)

Happy CD burning.

---

