---
title: "Permissions &amp; Users"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by betterspud on 2007-07-04
Hi. Am a complete newb with Linux, but am tryting to learn...

One thing I can't seem to get my head around though is how to get access with full permisions. I keep reading posts from other people that are having problems, but they are generally given a solution that involves changing user permissions using CHMOD & SUDO. I'd prefer to leave my user's permissions as they are until I am more confident that I'm not going to make some irreparable changes.
Is it possible to log onto Ubuntu (7.04) on an admin ID that has FULL permissions accross all files? I assume that I's need to set up a second user and CHMOD something in order to achieve it?

Any help would be appreciated.

BTW Does anyone know of a good, up-to-date resource where I can print off hardcopies of Linux documentation? It's be nice to be able to learn aout my OS when AFK...

Cheers

BetterSpuD

---

### Post by bukwirm on 2007-07-04
To enable root, check out [this page]("https://help.ubuntu.com/community/RootSudo").

---

### Post by brennydoogles on 2007-07-04
> **betterspud said:**
> Hi. Am a complete newb with Linux, but am tryting to learn...

One thing I can't seem to get my head around though is how to get access with full permisions. I keep reading posts from other people that are having problems, but they are generally given a solution that involves changing user permissions using CHMOD & SUDO. I'd prefer to leave my user's permissions as they are until I am more confident that I'm not going to make some irreparable changes.
Is it possible to log onto Ubuntu (7.04) on an admin ID that has FULL permissions accross all files? I assume that I's need to set up a second user and CHMOD something in order to achieve it?

Any help would be appreciated.

BTW Does anyone know of a good, up-to-date resource where I can print off hardcopies of Linux documentation? It's be nice to be able to learn aout my OS when AFK...

Cheers

BetterSpuD

There is a graphical way if you would prefer it.... If you go to System-> Administration-> Users and Groups. You really don't want to enable the root account on Ubuntu if you can avoid it, because you can really screw things up, and any files you make will belong to root rather than whomever you were trying to make it for. As for individual files, you can change ownership, as well as all permissions by right clicking, and going to permissions. If it is a file that you don't own, you can open a terminal and type ```
gksudo nautilus
``` and edit permissions on any file you wuold like!! i hope this helps!!!

---

### Post by mlentink on 2007-07-04
> **betterspud said:**
>  I'd prefer to leave my user's permissions as they are until I am more confident that I'm not going to make some irreparable changes.
> **betterspud said:**
> Is it possible to log onto Ubuntu (7.04) on an admin ID that has FULL permissions accross all files? 

I hope you see that these two wishes are incompatible? The whole 'X' security approach is designed to make sure no user by himself can do irreparable damage. In normal use, there is no need to have root privileges, in fact for someone who does not know what he or she is doing it can be dangerous because as root you can do everything. Including irreparable damage.
Even Mickeysoft finally understood this in Vista, with the introduction of UAC.

SO if you do choose to login as root, be very careful.

---

