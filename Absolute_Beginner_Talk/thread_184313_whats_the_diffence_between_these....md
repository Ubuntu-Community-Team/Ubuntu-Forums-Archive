---
title: "whats the diffence between these..."
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by smile-its-smiley on 2006-05-29
what are the differences between ubuntu, edubuntu, kubuntu, xubuntu?

---

### Post by gingermark on 2006-05-29
Ubuntu and Edubuntu use GNOME, the latter is optimised for educational needs, Kubuntu uses KDE and Xubuntu uses Xfce :)

---

### Post by Zerocool10482 on 2006-05-29
They have different desktop envirements 

GNOME.org
KDE.org
Xfce.org

Go to there sites to find out more and which one you want.

---

### Post by glotz on 2006-05-29
Ubuntu - GNOME - the simple desktop
Kubuntu - KDE - the sexy desktop
Xubuntu - Xfce - the lightweight desktop

---

### Post by mats-a on 2006-05-29
So that's all?
if everything else is the same I might as well switch to Kubuntu, there's gotta be something more to it, right?

It has to be harder to use or something

---

### Post by smile-its-smiley on 2006-05-29
so i like the look of kde but like the sound of the gnome, so is it possible to install ubuntu then install kde on top?

---

### Post by Engnome on 2006-05-29
[QUOTE=mats-a]So that's all?
if everything else is the same I might as well switch to Kubuntu, there's gotta be something more to it, right?

It has to be harder to use or something[/QUOTE]

Dont have to switch, can use both at the same time.

to install kde

sudo apt-get install kubuntu-desktop

---

### Post by gingermark on 2006-05-29
Put very simply:

GNOME focuses on simplicity and usability.
Xfce is like GNOME, but lightweight and fast.
KDE is very configurable - almost anything you imagine can be changed via the GUI, which is great for some people, whilst others consider it bloat.

Of course as widely used DEs they all strive for ease of use.

---

### Post by gingermark on 2006-05-29
[QUOTE=Engnome]Dont have to switch, can use both at the same time.
to install kde
sudo apt-get install kubuntu-desktop[/QUOTE]
I would advise doing ```
sudo aptitude install kubuntu-desktop
``` instead.

Then, if you decide you don't like it ```
sudo aptitude remove kubuntu-desktop
``` will remove it all again (using apt-get doesn't do this).

---

### Post by aysiu on 2006-05-29
Listen to Gingermark.

Step-by-step instructions are here, too:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

A fairly unbiased look at KDE v. Gnome is here:
[http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)

---

