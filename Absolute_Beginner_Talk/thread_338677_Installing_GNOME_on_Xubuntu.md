---
title: "Installing GNOME on Xubuntu"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-01-14
Hi,

I want to install GNOME on my XUbuntu 6.10.  When I tried to install the *ubuntu-desktop* meta package it wanted to remove 

evince-gtk 
gcalctool-gtk 
xubuntu-system-tools 

I'd rather this didn't happen.  If I install *ubuntu-desktop* will I be able to reinstall the above packages without trouble?  And if so, should I expect any adverse effects of having these packages alongside GNOME?

Thank you.

---

### Post by maxamillion on 2007-01-14
i think all it wants to do is replace them with the gnome counterparts.

Xubuntu attempts to use applications that don't require, or require a minimal amount of, gnome-libs and therefore the gcalctool-gtk will (or should) just be replaced by gcalctool (which is the standard package depending on gnome-libs and not just on gtk libraries).

As far as removing xubuntu-system-tools ... you might be able to re-install it but i'm not entirely sure because I have never attempted it.

---

### Post by aysiu on 2007-01-14
Could be *aptitude* trying to act too smart?

What method are you using to install Gnome?

---

### Post by x1a4 on 2007-01-14
> **aysiu said:**
> Could be *aptitude* trying to act too smart?

What method are you using to install Gnome?

Synaptic.

---

### Post by x1a4 on 2007-01-14
I guess the best route is to do it and see what happens.  Bitch of it is that I got my XUbuntu tweaked to perfection at the moment and don't want to screw it up.  Having said that, I do want to enhance it further.

---

### Post by DougieFresh4U on 2007-01-14
Leave it alone :)

---

### Post by psycosmyth on 2007-01-14
You can use apt-get install gnome.
You will replace those programs you listed but Xfce uses them just fine, The base gnome is best to use rather than the ubuntu-desktop. I have a base version of KDE, it has no junk and is happy with XFCE being around too. 
Do you want a Gnome look or just the apps?

---

### Post by psycosmyth on 2007-01-14
I checked synaptic but I did'nt see a "base" version. The Gnome and the Gnome desktop entries are basicaly the same.
I used gnome with xfce for as long as I had Dapper with no conflicts. The fact it has so many apps is the downside since it does slow down a little.

---

### Post by Pobega on 2007-01-14
sudo aptitude install gnome-core

It shouldn't need to remove anything as far as I know.

---

### Post by x1a4 on 2007-01-15
> **DougieFresh4U said:**
> Leave it alone :)

Why?  Even if I do mess things up, the best way to learn is by doing repairs, though I much rather for things to go smoothly.  Besides, it is possible to do it--isn't it?  Also, Ubuntu is supposed to be easy.  The reason those packages are in the repository is for people to install additional features.  Right?

---

### Post by x1a4 on 2007-01-15
> **psycosmyth said:**
> You can use apt-get install gnome.
You will replace those programs you listed but Xfce uses them just fine, The base gnome is best to use rather than the ubuntu-desktop. I have a base version of KDE, it has no junk and is happy with XFCE being around too. 
Do you want a Gnome look or just the apps?

Mostly for the look, some additional functionality and because I feel like it.  Xfce can run GNOME (and KDE for that matter) applications just fine.  This includes applications which run in the tray, as Xfce has panel applets which support GNOME and KDE tray applications.

---

### Post by x1a4 on 2007-01-15
Okay, I just said to myself, "The smeg with this," and installed the *ubuntu-* and, while I was at it, *kubuntu-desktop* meta packages and at first glance everything seems fine.  

Over the last two years I've installed a number of distributions, but for one reason or another I got rid of them and installed something else.  It was fun for a while but now I just want one distribution and stick with it.  Barring serious, unsolvable problems it's possible Ubuntu might the one.

---

### Post by Pobega on 2007-01-15
Those meta packages can cause some problems; If you want to try out another DE without switching Ubuntu distros you should try gnome-core and kde-core, they don't mess with your splash screen/login screen and still enable you to use the DE.

---

### Post by x1a4 on 2007-01-16
> **Pobega said:**
> Those meta packages can cause some problems; If you want to try out another DE without switching Ubuntu distros you should try gnome-core and kde-core, they don't mess with your splash screen/login screen and still enable you to use the DE.

Now he tells me :) 

As I said in my earlier post I've already done it, and just as quickly--as I jumped the gun and installed the ubuntu and kubuntu meta packages--removed them.  Things just didn't seem to click, bunch of little annoying errors here and there.  I'll follow your advice and install things one module at a time.  Although why I would want to do it other than for novelty purposes I can't image.  Xfce Rocks!  Despite it's limited features (though that's the point as it's meant to be small) for some undefinable reason I prefer Xfce over all other major environments.  GNOME is a close second, but I guess that's because Xfce is in part based on it.  

 :cool:

---

### Post by ItaniKnight on 2007-05-15
> **Pobega said:**
> sudo aptitude install gnome-core

It shouldn't need to remove anything as far as I know.

I've done this (well, I'm doing it as we speak) and I'm wondering: does this just meant that GNOME applications will run under xfce? As you said, it doesn't want to remove anything, but I'm curious as to what I need to do next.

**Edit:** OK, so I just went ahead and did it, and I'm happy to say that it works really well. I'm unable to remove some programs (like, for example, Mousepad (because of gedit!)) because it wants me to remove the *xubuntu-desktop*... Not something I want to do. But, if nothing else, it works like a charm. So, I got GNOME in xfce! Result.

---

### Post by vandorjw on 2008-06-16
> **Pobega said:**
> sudo aptitude install gnome-core

It shouldn't need to remove anything as far as I know.

I did this and it worked good, so far at least.
I'll report back if I notice problems or if it broke some applications.

---

