---
title: "Packages unavailable/missing/obsoleted etc."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-21
I am trying to install flashplugin-nonfree, mplayer, and mozilla-mplayer so I can use flash and the mplayer plugin for firefox.  One problem, when I do:

> $ sudo apt-get install flashplugin-nonfree

It says:

> Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

I have all the sources on my source list uncommented, I even added one for Opera (BTM the stable package seems to be broken...).  Where do I need to find these packages?

---

### Post by aysiu on 2006-06-21
It usually means you have conflicting repositories.

I'd get a fresh sources.list and add the Opera repository to that:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

### Post by WADemosthenes on 2006-06-21
[QUOTE=aysiu]It usually means you have conflicting repositories.

I'd get a fresh sources.list and add the Opera repository to that:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```[/QUOTE]

Worked perfectly, thanks.

---

