---
title: "Install gnome 2.22 clock in ubuntu 7.10"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-03-26
Is there a way to get the standard clock from gnome 2.22 (the one with the international clocks and all) in gutsy?

---

### Post by LowSky on 2008-03-26
short answer is yes, see my second post
or wait a month and upgrade to Hardy Heron

---

### Post by billgoldberg on 2008-03-26
I hope there would be a way, but well, it's not the end of the world.

A month is a long time.

---

### Post by LowSky on 2008-03-26
look what I found

> **whiprush said:**
> I made an intlclock .deb that is hosted on a launchpad personal package archive:

deb [http://ppa.launchpad.net/jorge/ubuntu](http://ppa.launchpad.net/jorge/ubuntu) gutsy main restricted universe multiverse

in /etc/apt/sources.list should do the trick. Or you can get the i386 or AMD64 debs directly here:

[http://ppa.launchpad.net/jorge/ubuntu/pool/main/i/intlclock/](http://ppa.launchpad.net/jorge/ubuntu/pool/main/i/intlclock/)

EDIT: Forgot to mention, you run it by right clicking on the panel, then Add to Panel, and choose the International Clock.

---

