---
title: "Enabling KDE in Gutsy"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-12-05
Hey,

OK, so I'm using Ubuntu (Gutsy).

Does anyone know if I can change from GNOME to KDE without having to install Kubuntu?!


CosmicFlux

---

### Post by 449 on 2007-12-05
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Or if you just want the core files use:

> sudo apt-get install kde-core

---

### Post by CosmicFlux on 2007-12-06
OK, thanx. 

So if I want to remove it again, what's the command-line code?

---

### Post by forestpixie on 2007-12-06
I'd use aptitude (well I did :) ) to install 

```
sudo aptitude install kubuntu-desktop
```

to remove

```
sudo aptitude remove kubuntu-desktop
```

---

### Post by CosmicFlux on 2007-12-06
Hmm when I use that command it says everything has been removed but there are still KDE applications in the menus, like Konsole and Konquerer.

---

### Post by forestpixie on 2007-12-06
what's left is it just some of them - or is it all of them

---

### Post by SOULRiDER on 2007-12-06
Try:
```
sudo aptitude purge kde-core
```

---

### Post by CosmicFlux on 2007-12-06
It's everything. I also tried:

**sudo aptitude purge kde-core**

but to no avail.

---

### Post by FuturePilot on 2007-12-06
Try this
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by maybeway36 on 2007-12-06
[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681")
> The problem here is that Aptitude is not removing
unneeded depends automatically.

---

