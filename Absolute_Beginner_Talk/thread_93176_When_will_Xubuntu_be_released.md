---
title: "When will Xubuntu be released?"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by bashhelp on 2005-11-21
I heard there is a Xubuntu (XFce + Ubuntu) under development.  I was wondering when will it be released?  They don't have a website yet, so I thought maybe some people here might know something.

---

### Post by az on 2005-11-21
In Breezy. you can install the base system, add universe to your list of repositories and then install xubuntu-desktop.

---

### Post by landotter on 2005-11-21
You can install it on a regular Ubuntu install by installing the xubuntu-desktop metapackage via Synaptic.

I've got it and Kubuntu installed to check out. Xubuntu is great on resources, Kubuntu is the best version of KDE I've ever used, but I still like the standard Ubuntu.

Xubuntu should be a wonderful match for older boxen.

---

### Post by bashhelp on 2005-11-21
I don't have high-speed Internet access at home.  So I cannot update or install anything from Ubuntu over the Net that is big.

I am asking someone else to burn it for me.  Therefore, I am looking for an official release of Xubuntu.

---

### Post by az on 2005-11-21
Bump this thread:
[http://www.ubuntuforums.org/showthread.php?t=90650](http://www.ubuntuforums.org/showthread.php?t=90650)

---

### Post by sigma2805 on 2005-11-21
does anyone know approximatly how much space one can save by installing xubuntu and then getting rid of gnome?

---

### Post by ofek on 2005-11-21
XFCE Is very light weight when compared to gnome.
Gnome takes about 120mb of ram on my system XFCE takes 80mb.
XFCE package is about 25mb and I think gnome is ALOT more.

---

### Post by az on 2005-11-21
[QUOTE=sigma2805]does anyone know approximatly how much space one can save by installing xubuntu and then getting rid of gnome?[/QUOTE]
You do not need to install gnome at all.

Just install the base system by typing server as you start the installation and then when you log in, enable the univderse repositories (nano /etc/apt/sources.list) and then type
sudo apt-get update
and

sudo apt-get install xubuntu-desktop
When you log into Xubuntu for the first time, you need to tell the login manager to use xfce since it will look for gnome by default, but that is about it.  I think it uses somehting like 600 megs of disk space for the total install.

---

