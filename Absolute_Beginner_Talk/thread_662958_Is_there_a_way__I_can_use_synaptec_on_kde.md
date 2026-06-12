---
title: "Is there a way  I can use synaptec on kde?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by natirips on 2008-01-09
Is there any way I can use gnome's synaptec on kubuntu (which uses kde), or at least, is there something alike synaptec (so I can see the list of all packages availible for "apt-get" because I don't know the names of all such packages). For example, if I want to install some codec, I don't think using brute force to figure out it's package name is a good idea...:(

---

### Post by kellemes on 2008-01-09
You can just run Synaptic from KDE just as you would from Gnome. It's no more than a frontend to the package-management-system.
If it's not installed you need to **sudo apt-get install synaptic** to get it.

---

### Post by natirips on 2008-01-09
> **kellemes said:**
> You can just run Synaptic from KDE just as you would from Gnome. It's no more than a frontend to the package-management-system.
If it's not installed you need to **sudo apt-get install synaptic** to get it.


It errors me out:

==================================
natirips@MagleniTabulator:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
natirips@MagleniTabulator:~$  
====================================
Or did I do something wrong?

---

### Post by kellemes on 2008-01-09
Ok, as far as I understand Kubuntu uses the **Adept Manager**, instead of Synaptic, search the menu's for this.

---

### Post by The Cog on 2008-01-09
K->System->Adept is the KDE equivalent. I think I prefer it, actually.

---

### Post by natirips on 2008-01-09
> **kellemes said:**
> Ok, as far as I understand Kubuntu uses the **Adept Manager**, instead of Synaptic, search the menu's for this.

Thanks alot. :)

---

