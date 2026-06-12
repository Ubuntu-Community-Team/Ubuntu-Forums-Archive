---
title: "[SOLVED] How do I install Gnome without an internet connection?"
date: 2008-12-10
forum: Arch and derivatives
---

### Post by Newuser1111 on 2008-12-10
How do I install Gnome(or KDE) without an internet connection?

---

### Post by DieB on 2008-12-10
try to get the alternate cd or get dvd from ubuntu, take them along to your pc and run install process. Or do u mean u have a running linux with neither nor gnome kde and u want to install that?

pls be more specific

---

### Post by smartboyathome on 2008-12-10
> **DieB said:**
> try to get the alternate cd or get dvd from ubuntu, take them along to your pc and run install process. Or do u mean u have a running linux with neither nor gnome kde and u want to install that?

pls be more specific

I think he means on Arch Linux. ;P

Anyway, on Arch, to install packages without an internet connection you would have to download the pkg.tar.gz from the server, and use (sudo/su) pacman -U pkgname.pkg.tar.gz.

If you need it to get an internet connection, though, I would recommend just downloading the Xorg packages (anyone know if they're included on the CD?) and WICD and then use WICD to connnect. I find that it succeeds where Arch's netcfg and iwconfig fail.

---

### Post by fwojciec on 2008-12-10
> **smartboyathome said:**
> Anyway, on Arch, to install packages without an internet connection you would have to download the pkg.tar.gz from the server, and use (sudo/su) pacman -U pkgname.pkg.tar.gz.

This would work, but the problem is that pacman -U doesn't resolve dependencies, so it's difficult using it to install things like gnome -- it works better for single packages.

The solution would be to download all required packages, put them in a local repository, and then install them with pacman -S.

---

### Post by kpkeerthi on 2008-12-11
Do this on an Arch machine that has acccess to internet:
```
pacman --cachedir /tmp/pkgs -Syw gnome gnome-extra
```

Then transfer the contents of /tmp/pkgs to /var/cache/pacman/pkg in the machine that needs it and run ```
pacman -U gnome gnome-extra
```

---

### Post by Newuser1111 on 2008-12-12
This isn't needed anymore, I got internet working on it by installing Windows on my other laptop.

> Do this on an Arch machine that has acccess to internet:I don't have any other computers that have Arch.


I just wanted to try doing it offline so my laptop wouldn't have to be at the router for a long time.

---

