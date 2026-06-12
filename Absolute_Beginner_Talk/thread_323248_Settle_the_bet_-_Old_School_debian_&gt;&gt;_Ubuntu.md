---
title: "Settle the bet - Old School debian &gt;&gt; Ubuntu"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by nickburns on 2006-12-21
I need help settling a bet.  

1.  Is it possible to take a fresh install of plain old debian (non-ubuntu flavor) and get it to apt-get to edgy eft desktop?  

2.  Or from edgy eft server version to the desktop version?

3.  If possible what are the steps?


nickburns

---

### Post by psycosmyth on 2006-12-21
I asked the same question not long ago but in inverse. I also aske in the Debian forums and all I got was "why?" and some mild lecture about policy.:mrgreen:

---

### Post by StormNet on 2006-12-21
I don't know about the first one, but as for the second one, it is fairly easy to add a GUI to the LAMP server edition of ubuntu.
```
sudo apt-get gnome-desktop
```That should get you the gnome desktop.

---

### Post by nickburns on 2006-12-21
But does this get me all the Ubuntu defaults?  do I need to change my /etc/apt/sources file?

---

### Post by az on 2006-12-21
> **nickburns said:**
> I need help settling a bet.  

1.  Is it possible to take a fresh install of plain old debian (non-ubuntu flavor) and get it to apt-get to edgy eft desktop?  

2.  Or from edgy eft server version to the desktop version?

3.  If possible what are the steps?


nickburns

1. yes
2. yes, probably easier
3. a)Install a version of Debian from a little while ago (make sure the version of libc6 is lesser in that version of Debian.  For example, you may have trouble dist-upgrading from an up-to-date Sid to Edgy, for example, since Edgy was released first.
b)  Change all the sources in sources.list to point to Edgy.  Leave to Debian references.  Make sure you have universe installed.
c) update and then install ubuntu-desktop.  Then dist-upgrade.  Keep dist-upgrading untill you are complete.

YMMV.  It's a painful trip, and you may need to tweak some stuff, but it can be accomplished.

---

### Post by nix4me on 2006-12-21
Just pick either debian or ubuntu.

It will save you alot of headaches.

Debian etch is very nice these days and so is Ubuntu edgy.  If you need bleeding edge without significant breakage, use Debian Sid.

nix4me

---

### Post by K.Mandla on 2006-12-21
> **azz said:**
> 1. yes
2. yes, probably easier
3. a)Install a version of Debian from a little while ago (make sure the version of libc6 is lesser in that version of Debian.  For example, you may have trouble dist-upgrading from an up-to-date Sid to Edgy, for example, since Edgy was released first.
b)  Change all the sources in sources.list to point to Edgy.  Leave to Debian references.  Make sure you have universe installed.
c) update and then install ubuntu-desktop.  Then dist-upgrade.  Keep dist-upgrading untill you are complete.

YMMV.  It's a painful trip, and you may need to tweak some stuff, but it can be accomplished.
Azz is right (as usual ;) ). I once jumped from Dreamlinux to Ubuntu in the same way. It was a long strange trip, but it can be done. They thought I was wacky on the Dreamlinux forums. :mrgreen:

---

