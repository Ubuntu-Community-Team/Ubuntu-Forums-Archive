---
title: "Why different apps for different desktops?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by 01000111 on 2008-01-28
:confused:

Okay... I've been using Ubuntu for a few months now, and have tried Ubuntu, Kubuntu and have settled on Xubuntu because of the performance.  However, I'm still confused about one thing (well, several, but just one for this post)...

There are apps for Ubuntu, apps for KDE, apps for Xubuntu and apps for all...  why?

Why isn't it that there are simply different desktop managers, and a pool of apps that work on all.  I am aware of shared libraries, et al, but still not clear on this.  A good example is that I like the Amarok music player, but want to use it on Xfce.  Why does it need to load a bunch of KDE stuff to work?

Remember, I'm fairly new at the whole Linux thing, so please keep the flames to a mild simmer.  :)

Thanks,

G.

---

### Post by nowshining on 2008-01-28
it depends on some libraries that kde has :) it's a dependency thing. One thing depends on another -

---

### Post by LaRoza on 2008-01-28
Ubuntu uses GNOME, which uses GTK libraries, and has official apps, like Nautilus. (The official browser is Epiphany, not Firefox)

Kubuntu used KDE, which uses QT.

Each one has a limited number of space on the CD, so it is quite restricted. 

When you have KDE running, many services of KDE are up, which makes KDE apps open without much pause, a more seamless desktop. GNOME is the same way. Having the DE, and the apps use the same libraries makes for a very seamless desktop with little bulk.

You can install any apps you wish though, but you will need the dependencies that are used by the apps.

QT and GTK aren't tiny, so there is a lot to be used by apps.

---

### Post by az on 2008-01-28
> **01000111 said:**
> 
There are apps for Ubuntu, apps for KDE, apps for Xubuntu and apps for all...  why?



Because there is not just one way to do something.

One strength of the free and open-source software development model is that there are no limitations to what you can do or how to do it.  There are guidelines, of course.  For example, there are usability guidelines that determine how a KDE application should behave so that it resembles and fits in with the other KDE apps, but that doesn't limit your freedom to make something work differently.

The drawback is that the software is not binary-compatible.  You can't write something, compile it and expect it to be able to run on every linux platform.  The advantage, though, is that when something is not tied-down to a promise to be compatible with something else, the program can run a lot more efficiently; not to mention the security benefits.

This method works really well.  The "best" way to do something is not set in stone.  That makes the software development be able to turn on a dime.  Again, that strength comes at the cost of a little extra complexity.  Fortunately, the distro of your choice should abstract all that from you.  You should be able to install and run amarok from xfce and not worry about what packages to run nor what shared libraries to load when you start it.

---

