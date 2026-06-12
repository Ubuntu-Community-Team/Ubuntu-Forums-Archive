---
title: "Removing ubuntu-desktop..."
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by chrisfay on 2006-09-22
Is it safe to apt-get remove ubuntu-desktop?

I installed it over the Dapper Server version and would like to remove it. That is, if it won't brake every package I've installed since.

---

### Post by Tomosaur on 2006-09-22
Yes, it is safe to remove, but it won't remove the other stuff it installs. Ubuntu-desktop is a dummy package.

---

### Post by chrisfay on 2006-09-22
> Yes, it is safe to remove, but it won't remove the other stuff it installs. Ubuntu-desktop is a dummy package.

Will it remove Gnome/GDM? I'm hoping to remove the gui.....

---

### Post by kidders on 2006-09-22
Yeah,

Like Tomosaur says, installing the graphical desktop architecture pulls in piles and piles of dependencies as well. As far as I can make out, Ubuntu's package manager doesn't provide you with a convenient way of removing these, like Gentoo's "emerge" manager can, for example. Technically, it's quite a tough thing to get right :-(

**Edit:** The Gnome/KDE GUIs are quite fragmented, spread over a number of packages. Removing each one would be tedious, but quite safe, imo.

---

### Post by chrisfay on 2006-09-22
In hignsight, would it have made it easier to aptitude install ubuntu-desktop vs apt-get in regards to removing the dependencies?

I really don't have a problem leaving the crap it installed, I just would like to have the system boot into the cli instead of gnome.

---

### Post by kidders on 2006-09-22
In that case, all you need to do is disable the display manager service. Just because it's installed doesn't mean you *have* to start it at boot :-)

---

### Post by chrisfay on 2006-09-22
True, I may just remove the gdm daemon and call it a day...

---

### Post by kidders on 2006-09-22
That may be the best option. After all, you may decide you want it again in a couple of months, or find a use for some of the graphics/multimedia dependencies. After having spent hours trying to kill them all, that would be annoying hehe.

---

### Post by JAwuku on 2006-09-22
If you want to remove all of Gnome on Ubuntu, take a look at the site [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

which gives you a long apt-get remove command.

If you, say want to reinstall ubuntu-desktop sometime in the future, you can use aptitude instead of apt-get or Synaptic. Aptitude will install all the dependencies like apt-get, but also adds recommended packages. On uninstalling, aptitude will also remove all dependencies of the package (providing they are not used by any other packages).

i.e. ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
to install ubuntu-desktop

and instead of the huge apt-get remove, you can simply issue the elegant ```
sudo aptitude remove
``` provided you have used aptitude to install it before.

---

