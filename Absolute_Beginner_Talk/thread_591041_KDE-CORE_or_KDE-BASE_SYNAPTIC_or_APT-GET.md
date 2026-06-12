---
title: "KDE-CORE or KDE-BASE? SYNAPTIC or APT-GET?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by d-_-b on 2007-10-25
lol. i think the title does a nice summary of my queries.
so i want to install ONLY the KDE interface. I dont want any of the programs that come default with KDE desktop environment (like what you would get when you install kubuntu-desktop or kde from synaptic). So which one do i have to install: Kde-core OR Kde-base?

also, which method of installation is better? through terminal apt-get OR through synaptic?

---

### Post by DutyDuty on 2007-10-25
I can't help you with the KDE questions, but I can tell you that most of the time, if you can install from source, then you will be happier, since the apps will run better on your system. As far as the comparison between apt-get and Synaptic, Synaptic may be better if you don't know the exact name of what you are looking for.

---

### Post by shae on 2007-10-25
kde-base has more features than kde-core.  Either method is acceptable.  Apt-get is through the command line and Synaptic is just a GUI frontend to apt-get.

---

### Post by d-_-b on 2007-10-25
so kde-base comes with SOME K software, whereas kde-core is purely JUST the interface and NO software?

---

### Post by mikewhatever on 2007-10-25
Check out these 
[http://packages.ubuntu.com/gutsy/kde/kde-core](http://packages.ubuntu.com/gutsy/kde/kde-core)
[http://packages.ubuntu.com/gutsy/kde/kdebase](http://packages.ubuntu.com/gutsy/kde/kdebase)

kde-core depends on kdebase (kde-base does not exist).
The installation result would be the same through both apt-get/terminal and synaptic.

---

### Post by Maestro23 on 2007-10-25
> **d-_-b said:**
> so kde-base comes with SOME K software, whereas kde-core is purely JUST the interface and NO software?

If you go into Synaptic and search for each package. It will tell you ecaclty what will be installed.

---

### Post by d-_-b on 2007-10-25
cool. thanks peeps

---

### Post by marco123 on 2007-10-25
Use aptitude e.g : sudo aptitude install kde-core

That way it's much easier to uninstall it.

Link: [http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)  It's kde-core you want.

---

### Post by aysiu on 2007-10-25
I would recommend *kde-core*, which is actually functional, as opposed to *kdebase*, which is pretty barebones to the point of being useless.

It doesn't matter if you install it with Synaptic or *apt-get*.

---

