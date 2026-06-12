---
title: "Help with XGL removal and apparently a bug"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by daberger on 2008-03-31
during a thread about fixing how to enable desktop effects i added an xgl file which i dont like because my system now runs slower and since then i have been getting a lot of error messages about gnome and i dont like it. i can use a temporary fix ```
SKIP_CHECKS=yes compiz
```
but i dont really like doing it every time i log in. on the other had i could create a session..........

but i really need to fix this bug and remove XGL and have the open source driver work instead and get my system functioning again. ty

---

### Post by spiderbatdad on 2008-03-31
I believe you'll find xserver-xgl in synaptic for easy removal.

Then you can reconfigure xserver...before starting all over...```
sudo dpkg-reconfigure -phigh xserver.xorg
```

---

### Post by daberger on 2008-03-31
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not install

any other ideas?

---

