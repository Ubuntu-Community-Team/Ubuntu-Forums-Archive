---
title: "Removing the gnome desktop"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-05-08
I recently installed the xubuntu-desktop to my laptop, it runs much quicker than the default gnome desktop on my old machine.

As well as being short on RAM, my laptop also has a small hard disk. So, I want to free up some disk space by getting rid of the gnome desktop.

I've read the HOWTO, I think by ayisu? about how to get rid of the gnome desktop if you've just switched to kubuntu-desktop. But that's about getting rid of the _whole_ ubuntu-desktop and running the KDE apps instead.

I don't want to get rid off _all_ my old apps.For instance, I want to keep Firefox. But I believe that would go, as part of ubuntu-desktop. And the gimp. And rhythmbox. And I'm not really sure what else.

I want to get rid of the bits of gnome I don't need on my disk anymore - I'm happy with the xfce stuff - but I don't want to go with all  the xubuntu-desktop apps. That make any sense? And can someone tell me the names of the gnome-related stuff that I can remove without screwing up firefox etc?

---

### Post by hw-tph on 2006-05-08
I think what you are referring to is that Ayisu recommends aptitude over synaptic or apt-get. If a package is installed using aptitude and you decide to uninstall it later, aptitude will uninstall the dependancies - if not required by another package.

I don't think this works for the default set of installed applications since these are not installed using aptitude. The ubuntu-desktop package is a meta-package. It doesn't provide anything by itself but just lists dependancies - the default packages. If you uninstall any of these packages, ubuntu-desktop will be broken and uninstalled (but in most cases your desktop will still be perfectly usable) automatically. First thing I do after installing Ubuntu is removing the font packages I don't need or use (a lot of asian fonts that I can't make any sense of are part of ubuntu-desktop for instance). This doesn't change my own computing experience, it just removes the clutter.

You can find the ubuntu-desktop package in aptitude and remove the parts of it which you don't like. That is probably the easiest course of removing the Gnome components. If somebody else knows a clean quick way I'm all ears. :)


Håkan

---

### Post by catlett on 2006-05-08
I don't know anything about this, so this is just a thought. What about going into Synaptic Package Manager and taking out or taking parts out  of the Gnome Desktop Environment? It looks like you can pick and choose. Plus Synaptic will prompt you if it is uninstalling other packages as part of another uninstall. No experience with this just a thought.

---

