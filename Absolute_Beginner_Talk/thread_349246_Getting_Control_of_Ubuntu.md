---
title: "Getting Control of Ubuntu"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-01-29
I want a desktop that doesn't have any "useless" programs on it.
Every time I try to uninstall something that came pre-loaded on my computer (such as, firefox, thuderbird, etc.) it will tell me I have to uninstall the whole ubuntu-desktop!

I wish there was an easier way to put the stuff I wanted onto my desktop, and not some "premade" configuration.

Does ubuntu offer some kind of core, where it only comes with the bare minimum (and lets me choose which WindowManager, what programs I want, etc.)

I could think of Instaling the SERVER edition, but how do I get the WindowsManager I want (KDE, Ubuntu, XFCE, etc.) without all of the crap attached?
:confused:   Thank you very much.

---

### Post by bward1 on 2007-01-29
You could install the server version and then use fluxbox as your window manager and pick and choose which applications you want.  You can do```
apt-get install fluxbox
``` to get it.  Once you have a window manager Synaptic is your friend.

---

### Post by p!=f on 2007-01-29
> **chris062689 said:**
> I want a desktop that doesn't have any "useless" programs on it.
Every time I try to uninstall something that came pre-loaded on my computer (such as, firefox, thuderbird, etc.) it will tell me I have to uninstall the whole ubuntu-desktop!

Well, what's useless for you may be useful for others. ;)
Ubuntu-desktop is just a metapackage. It won't remove whole desktop if you uninstall it.

> **chris062689 said:**
> 
I wish there was an easier way to put the stuff I wanted onto my desktop, and not some "premade" configuration.

Yes, this predefined configuration helps people which don't know what they want and how the application (package) is called.

It's easy as
```

sudo apt-get install what-you-want

```

> **chris062689 said:**
> 
Does ubuntu offer some kind of core, where it only comes with the bare minimum (and lets me choose which WindowManager, what programs I want, etc.)

Again, how can it know what you want? There are over 20 000 packages to offer.
```

apt-cache show ubuntu-{minimal,standard}

```

---

### Post by NeoLithium on 2007-01-29
Removing ubuntu desktop just gets rid of the ubuntu stuff; however if you decide to use the server install; you can just install whatever you want, be it fluxbox, kde-core or gnome-core; but make sure you also remember to install xorg and xserver-xorg as well; otherwise it won't start; plus you have to install your login manager if you don't want to do the command line login with startx (GDM is the gnome one; KDM kde, as you can guess); Using the server is good for having a bare-bones install; but you should really have a decent grasp of setting the things up to make it as painless as possible.

---

### Post by 3rdalbum on 2007-01-30
If it says that it will remove "ubuntu-desktop", don't worry. Ubuntu-desktop is just a 10 kilobyte package - removing it will not remove any other packages.

---

### Post by jvc26 on 2007-01-30
If you are doing a dist-upgrade I think that is the only time the ubuntu-desktop meta package is used. To my knowledge you can just remove it and thats fine.
Il

---

### Post by chris062689 on 2007-01-30
So.. to do a barebones install...
I would have to install the server....
THEN...

apt-get install gnome-core
apt-get install kde-core
apt-get install fluxbox
- To install the Windows Manager.

apt-get install xorg
apt-get install xserver-xorg
- To install the windows managers (do I need both?)

apt-get install gdm (for gnome login manager)
apt-get install kdm (for kde login manager)


Is this all I need?
What exactly is installed with the gnome-core and/or kde-core?
Thank you!

---

### Post by PriceChild on 2007-01-30
gnome-core, kde-core or fluxbox will automatically install X and the *dm.

---

### Post by chris062689 on 2007-01-30
Ah ok, thank you!
I'll try it when I get home (and after I install Ubuntu core).

---

### Post by chris062689 on 2007-01-30
What's better to use to install the server?
The alternative CD, or the live installer CD?

---

