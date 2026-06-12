---
title: "Running Ubuntu and Kubuntu at same time"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by planet-reptile on 2007-11-29
Hi.

I followed this advise and installed KDE desktop at the same time as i have Ubuntu 7.10.

I followed this:
sudo aptitude update && sudo aptitude install kubuntu-desktop

But i don't like it and i want to remove Kubuntu so i unly have Ubuntu. How do i remove it so i only have Ubuntu 7.10?

---

### Post by fineas on 2007-11-29
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by mvanes on 2007-11-29
Just go to gnome.org and follow the install for download. [[http://www.gnome.org/start/stable/]](http://www.gnome.org/start/stable/])

I'm guessing that is what you're after anyway...

---

### Post by HermanAB on 2007-11-29
At the same time:
Run Ubuntu with Gnome, then open a terminal and type:
$ kicker

Then you'll have three tool bars, two for Gnome and one for KDE.

Cheers,

Herman

---

### Post by mcduck on 2007-11-29
> **planet-reptile said:**
> Hi.

I followed this advise and installed KDE desktop at the same time as i have Ubuntu 7.10.

I followed this:
sudo aptitude update && sudo aptitude install kubuntu-desktop

But i don't like it and i want to remove Kubuntu so i unly have Ubuntu. How do i remove it so i only have Ubuntu 7.10?

Simple 'sudo aptitude remove kubuntu-desktop' should do what you want. ;)

---

### Post by natehatewindows on 2007-11-29
```
sudo aptitude removed xbuntu-desktop
```

in gnome of course. restart and you sould only have gnome :)

---

### Post by planet-reptile on 2007-11-29
Thank you folks :)

---

