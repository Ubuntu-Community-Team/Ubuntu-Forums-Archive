---
title: "GNOME == KDE equivalent commands"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Geoneil on 2006-05-13
I'm a Kubuntu user and I've noticed a few things...

{1} These forums see a bit more action than the Kubuntu forums, both the Kubuntu section here and at [http://www.kubuntuforums.net](http://www.kubuntuforums.net) .
{2} Most of the solutions here refer to the terminal (which always appears to be common to all *buntu distros) but there are some that refer to GUI utilities, these always to GNOME specific utilities (only natural I suppose, Ubuntu is a GNOME-based distro)
{3} I've gone over to [http://dot.kde.org](http://dot.kde.org) and noticed the story concerning Ubuntu management declaring [greater support for KDE in the future](http://dot.kde.org/1147097810/1147107248/1147108128/) (likely promising to make Kubuntu even better than it is, I've heard good things about Dapper's beta releases and look forward to it coming out) but there seems to be a lot of doubt about that, Ubuntu appears to be seen by the peoiple there as a GNOME distro and Kubuntu the lesser-known KDE based little sister.
{4} A search of the forum for "GNOME KDE equivalent" (for what I'm about to kick off) didn't turn up what I wanted (a translation of GNOME specific commands to Linux noobs who happened to download Kubuntu instead.

I've been nervous about asking this as I always thought it was a silly question and that such a thread would already exist but I'll ask it anyway...

{1} How much the advice in **this** forum applies to Kubuntu?  Am I correct in assuming pretty much all as the two distros are the same bar the DE?

{2} Could we have a sticky "translation table" in the forum explaining to (K/X)ubuntu users what the equivalent to the GNOME apps mentioned here are...

In my time with Kubuntu, I've worked out (or am assuming) the following...

Synaptic == Adept
gedit == kwrite
gksudo == kdesu
sudo (in regards to anything that needs the GUI) == kdesu

Can anyone add to or correct the above list?  Heck, you can even move (I'd rather you copied tbh) this to the Kubuntu section if you want

---

### Post by mostwanted on 2006-05-13
Synaptic == Adept
gedit == kate
gksudo == kdesu

You nailed it except sudo is a terminal thing and is the same in both KDE and Gnome and kwrite is equivalent to AbiWord. And it's not really "commands", it's just applications. When you need to open a text file and the instructions say to open it with gedit, your common sense should instruct you with what to replace it with :) There's really no need for any conversion table.

---

### Post by Geoneil on 2006-05-13
Perhaps, but you can't naturally assume common sense in anybody, I can *guess* which KDE packages relate to the GNOME packages stated in this forum.  

I just suppose that it has to be made clear that all the *ubuntus are the same underneath the graphics and that complete noobs (again, such as myself and anyone else whose come straight from either Windows or no computer experience at all) need a little reassurance that they're guessing right :)

---

### Post by catlett on 2006-05-13
Kubuntu and Ubuntu are the same linux distro. The difference is in the window manager/desktop. The both have the same debian based ubuntu server system. Then you add the gui manager, kde or gnome to get kubuntu or ubuntu respectively. The commands are the same it is the applications that are different.
For example you open a text file with gedit in gnome, with kwrite in kde but you will use the same command in the terminal to make a change.
You can have both managers on your system. If you have gnome just enter ```
sudo apt-get install kubuntu-desktop
``` to get kde. If you have kubuntu just enter ```
sudo apt-get install ubuntu-desktop 
``` to get gnome.
When you start your computer you can choose between them by hitting on the "sessions" option. Then hitting on gnome or kde.

---

### Post by dabear on 2006-05-13
[QUOTE=catlett]Kubuntu and Ubuntu are the same linux distro. The difference is in the window manager/desktop. The both have the same debian based ubuntu server system. Then you add the gui manager, kde or gnome to get kubuntu or ubuntu respectively. The commands are the same it is the applications that are different.
For example you open a text file with gedit in gnome, with kwrite in kde but you will use the same command in the terminal to make a change.
You can have both managers on your system. If you have gnome just enter ```
sudo apt-get install kubuntu-desktop
``` to get kde. If you have kubuntu just enter ```
sudo apt-get install ubuntu-desktop 
``` to get gnome.
When you start your computer you can choose between them by hitting on the "sessions" option. Then hitting on gnome or kde.[/QUOTE]
Nono! Do not use apt-get to install the *-desktop packages!
Use aptitude instead. This way you can remove all the dependencies when/if you wanna uninstall the *-desktop package of your choice.
```

sudo aptitude install ubuntu-desktop 

```
```

sudo aptitude install kubuntu-desktop 

```

---

### Post by TheGreenMutville.edut on 2006-05-16
ok so its this more like a duel boot ( i know its not just using it as an anolgy), is it a  change in the shell properties,  or is this some thing else?

---

