---
title: "Crossing over from Kubuntu"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by fester225 on 2007-03-03
I started Linux in Debian, then was advised to try Kubuntu. I like Kubuntu, but I can't get it to upgrade the KDE desktop. Now I've got my second Ubuntu 6.10 CD, which starts, but doesn't complete the install, (this one was burned using the online utility suggested).

Getting into Ubuntu started after discovering no obvious way of installing Shockwave, or anything else. There is no standard utility for installing the open source programs available, and no way to ask for one.

I decided to got through the Ubuntu knowledgebase for help. That gave me Gaim and System -> Administration -> Synaptic Package Manager, which doesn't exist in Kubuntu.

Let's start with the basics;
    1. how do I install Shockwave on Kubuntu?
    2. how do I cross over from Kunbuntu to Ubuntu?
    3. is there going to be a way to update/upgrade in Ubuntu?
    4. is there going to be a standard way to install programs in Unbuntu?

---

### Post by teaker1s on 2007-03-03
terminal```
 sudo apt-get update
sudo apt-get install synaptic
``` will get you synaptic if you have internet connection

to launch it
```
gksudo synaptic
```

---

### Post by Iarwain ben-adar on 2007-03-03
I beg to differ with teaker1s:

Adept is a Synaptic clone for KDE. (a nice one, although i always use commandline)

To update (in Adept it is quite straight-forward):
```
sudo aptitude update && sudo aptitude upgrade
```

This will update your list, and download the updates and install them.

A standard way to install stuff: enable the multiverse repo's (search ubuntu knowledgebase for that) and search and install via Adept (or commandline if you like)

And if you want to switch from KDE to Gnome (Kubuntu to Ubuntu), make sure you have both
DE's installed
```
 sudo aptitude install ubuntu-desktop kubuntu-desktop
```

Then just log out, choose a different session, and login :D


Iarwain

---

### Post by Dylnuge on 2007-03-03
Just install ubuntu-desktop in Synaptic. Then decide whether you want KDM (your current login screen) or GDM (GNOME Login Screen).

Reboot. Click Options, Change Session, and choose GNOME.

Updates, installation, shockwave, etc, are all the same in Ubuntu. The only difference is the desktop. You can still use KDE if you want by clicking Options, Change Session, KDE in GDM.

---

### Post by dwblas on 2007-03-03
This link says that Shockwave is not available for Linux, so you have to use Wine to get it to work.
[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

---

