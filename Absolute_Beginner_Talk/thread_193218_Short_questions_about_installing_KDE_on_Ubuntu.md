---
title: "Short questions about installing KDE on Ubuntu"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-06-09
I have read [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html) and it is pretty good.

What I don't know is how much disk space do I need in order to install on top of my Ubuntu?

(I saw there are two versions to choose from too: )
"Once you've updated, go ahead and install KDE with the command sudo aptitude install kubuntu-desktop.

The kubuntu-desktop metapackage will install the standard Ubuntu version of KDE with the appropriate artwork and defaults favored by Ubuntu.

If you want a lighter-weight version of KDE, do sudo aptitude install kde-core instead. "

Would most of the programs installed from Ubuntu get transferred automatically to KDE as well (and that it won't install two copies of them)?

Thanks!

---

### Post by Jagot on 2006-06-09
According to Synaptic, installing kubuntu-desktop on top of my current Ubuntu installation will use 472MB.

It won't install two copies of them.  You'll be able to access all your KDE packages from Ubuntu and all your GNOME packages from Kubuntu, but obviously Kubuntu has a whole lot of other programs that are used to achieve the same things as those in Ubuntu.

---

### Post by wombat20 on 2006-06-09
If you really need it to be lightweight, try XFCE (Search for it in Synaptic).

---

### Post by boom2k1 on 2006-06-09
Thanks!
That's helpful :)

Does anyone know about installing the light weight version of KDE? What will not be included in the light weight version?
How much space would it need?

What is the main advantage of 
XFCE
besides it is small??

---

### Post by catlett on 2006-06-09
XFCE installed in ubuntu is called xubuntu [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by aysiu on 2006-06-09
Before you do ```
sudo aptitude install *packagename*
``` you'll get a list of what packages will be installed *and* how much additional space those packages will take up--not always, but certainly for huge metapackages.

You'll then be asked if you want to proceed or not. If you say "no," then the installation won't happen.

For a light-weight KDE, try ```
sudo aptitude update
sudo aptitude install kde-core
``` You'll see exactly what packages will be installed and how much space it will take up.

---

