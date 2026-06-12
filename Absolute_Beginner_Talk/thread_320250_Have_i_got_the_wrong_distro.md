---
title: "Have i got the wrong distro?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by benjjo on 2006-12-17
I've just been looking at the screen shots of Edgy and mine doesn't look like that!
I only have applications available as a menu item and not the "places" + "system" dropdown menus. 
I thought this was an Ubuntu idea because im running fc6 on another machine and it seems far easier to work with. Untill, that is,  i see [these]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntu%206.10") screen shots and realise that you too have the same menu categories.
Is XUbuntu some kind of compact version of Edgy? Or have i stuffed up the install?

---

### Post by igknighted on 2006-12-17
> **benjjo said:**
> I've just been looking at the screen shots of Edgy and mine doesn't look like that!
I only have applications available as a menu item and not the "places" + "system" dropdown menus. 
I thought this was an Ubuntu idea because im running fc6 on another machine and it seems far easier to work with. Untill, that is,  i see [these]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntu%206.10") screen shots and realise that you too have the same menu categories.
Is XUbuntu some kind of compact version of Edgy? Or have i stuffed up the install?

Xubuntu is edgy with a lightweight (read: decreased graphics, increased performance on low-end systems) desktop environment known as Xfce.  The screen shots you see are the default Ubuntu D.E., Gnome.

---

### Post by macogw on 2006-12-17
> **benjjo said:**
> I've just been looking at the screen shots of Edgy and mine doesn't look like that!
I only have applications available as a menu item and not the "places" + "system" dropdown menus. 
I thought this was an Ubuntu idea because im running fc6 on another machine and it seems far easier to work with. Untill, that is,  i see [these]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntu%206.10") screen shots and realise that you too have the same menu categories.
Is XUbuntu some kind of compact version of Edgy? Or have i stuffed up the install?

Ubuntu uses GNOME for the Desktop Environment.  Kubuntu uses KDE.  Xubuntu uses Xfce.  Each desktop environment uses different amounts of system resources, has a different layout, and has different apps with it.  GNOME is the one in FC and in the screenshots you saw.  KDE uses the most system resources and has a menu from the bottom and only one panel, like Windows.  Xfce is a very lightweight DE which is similar to GNOME.  That's what's on Xubuntu.

---

### Post by msak007 on 2006-12-17
> **benjjo said:**
> I've just been looking at the screen shots of Edgy and mine doesn't look like that!
I only have applications available as a menu item and not the "places" + "system" dropdown menus. 
I thought this was an Ubuntu idea because im running fc6 on another machine and it seems far easier to work with. Untill, that is,  i see [these]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntu%206.10") screen shots and realise that you too have the same menu categories.
Is XUbuntu some kind of compact version of Edgy? Or have i stuffed up the install?
Based on you last question, it seems you're using Xubuntu? While at the core it is the same distro as Ubuntu, Xubuntu is meant to be more lightweight and more suited for older machines so it runs on XFCE, a lightweight desktop manager that is an alternative to Gnome (which is what Ubuntu runs on). You won't see the same menu structure and options because it is a different desktop environment. So at this point you have 2 options:

1. Download and install an Ubuntu (not Xubuntu)
2. Simply install the package "ubuntu-desktop". This is the metapackage that installs everything normally installed in an Ubuntu install. Use [this]("http://www.psychocats.net/ubuntu/gnome") page as a reference. It specifically talks about installing Ubuntu in conjunction with Kubuntu, but the concept is the same.

EDIT: Seems I'm too slow and a couple others beat me to it :).

---

### Post by igknighted on 2006-12-17
> **macogw said:**
> Ubuntu uses GNOME for the Desktop Environment.  Kubuntu uses KDE.  Xubuntu uses Xfce.  Each desktop environment uses different amounts of system resources, has a different layout, and has different apps with it.  GNOME is the one in FC and in the screenshots you saw.  KDE uses the most system resources and has a menu from the bottom and only one panel, like Windows.  Xfce is a very lightweight DE which is similar to GNOME.  That's what's on Xubuntu.

This is not the case.  The KDE and gnome looks you describe are simply the default settings.  Gnome can have a single menu and only one panel, and KDE can have multiple panels and multiple menus.  The big difference is in the libraries.  Gnome is built with GTK libraries, KDE is built with QT lbraries.  KDE tends to use more system resources initially because it loads lots of libraries, but if you are like most users and run many programs at the same time, KDE will usually outperform gnome because KDE apps share the common libs better than gnome does.

---

### Post by benjjo on 2006-12-17
Cool, thanx guys. I'm going with a fresh install i think. I'm running XUbuntu on a Laptop (presario V2000), not the greatest machine in the world but certainly not the oldest.
I chose Xubuntu bec it came with a magazine and the live boot was so successful it sold me. 
Anyway, back to the drawing board (well bittorrent in this case).
Thanx again, that explained alot.

---

### Post by macogw on 2006-12-17
> **igknighted said:**
> This is not the case.  The KDE and gnome looks you describe are simply the default settings.  Gnome can have a single menu and only one panel, and KDE can have multiple panels and multiple menus.  The big difference is in the libraries.  Gnome is built with GTK libraries, KDE is built with QT lbraries.  KDE tends to use more system resources initially because it loads lots of libraries, but if you are like most users and run many programs at the same time, KDE will usually outperform gnome because KDE apps share the common libs better than gnome does.

Oh, I know you can change it, but if you use Google Images and search for kde you'll see mainly the default layout.  Ditto for the others.  Anything can be made to look like anything else, but if you're looking up screenshots, you'll find an overwhelming number that are default.

I don't like KDE apps as much as Gnome ones, with the exception of KTorrent.  I've also heard that the difference developmentally is that in Gnome they write lots and lots of libraries so when you need an app, it's a simple process to make one, while in KDE they focus more on the applications.

Oh, the OK and Cancel buttons switch sides between KDE and Gnome.

---

### Post by chrisfay on 2006-12-17
> Anyway, back to the drawing board (well bittorrent in this case).

Why don't you just install the desktop you 'do' want, instead of starting over from scratch.




**EDIT:** Sorry msak007, I didn't realize you had already suggested that until after I posted this.....

---

### Post by seijuro on 2006-12-17
> **macogw said:**
> KDE uses the most system resources and has a menu from the bottom and only one panel, like Windows.

Just thought I'd point out for benjjo that this is the default config both Gnome and Kde can add or remove more panels to give you whatever floats your boat look. I have my Kde panels split into top and bottom like the default Ubuntu install.

---

### Post by benjjo on 2006-12-17
>  Why don't you just install the desktop you 'do' want, instead of starting over from scratch.

I'm also having too many issues with the dodgy [PICNIC]("http://www.urbandictionary.com/define.php?term=picnic") install of Xubuntu.  If you see some of the other posts ive put up you'll understand why.
I think i've got a better chance at a smoother install a second time around.

---

