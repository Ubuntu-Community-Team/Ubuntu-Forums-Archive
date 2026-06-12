---
title: "ubuntu / kubuntu"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by cyberlite on 2006-07-09
What is the diffence between ubuntu & kubuntu????? is it one is gnome the other kde?????

---

### Post by Sonic Alpha on 2006-07-09
Yeah, there are a few other program differences from what I can tell from the Live CDs, but you basically hit the nail on the head.

---

### Post by aysiu on 2006-07-09
From the Kubuntu website: > Kubuntu is the first Ubuntu derived distribution. Our Kubuntu CDs are made up of Ubuntu's base plus KDE. You can get exactly the same effect by installing Ubuntu and adding the KDE packages (and removing the Gnome packages) from the Ubuntu archives.

---

### Post by skizz on 2006-07-09
Well,

Ubuntu is based on GNOME and
Kubuntu is based on KDE.

GNOME and KDE are graphical interfaces, if you didn't know.

Hope that enlightens your mind a little.

Cheers, 

A.

---

### Post by Endow on 2006-07-09
Can I have both installed and choose which to use?

Btw aside from visual diferences (and even those i don't understand...I mean what are visual differences?Different themes???I can get any theme online so why would I need KDE??...) what esle is different?Any philosophic difference?

---

### Post by FredB on 2006-07-09
> **Endow said:**
> Can I have both installed and choose which to use?

You can try them (live CD) and chose the one you prefer.

To simplify a lot :

- Gnome = MacOS like interface
- KDE = Windows like interface

> 
Btw aside from visual diferences (and even those i don't understand...I mean what are visual differences?Different themes???I can get any theme online so why would I need KDE??...) what esle is different?Any philosophic difference?

You can install Ubuntu and install on it KDE (from kubuntu) or the opposite.

The *best* is to try both and choose the one you prefer.

---

### Post by cyberlite on 2006-07-09
Thx Fredb I have already, personaly I like kde now that I've installed it.
It just looks better to me.

---

### Post by aysiu on 2006-07-09
[http://www.psychocats.net/ubuntu/kdegnome.html](http://www.psychocats.net/ubuntu/kdegnome.html) explains the differences.

---

### Post by digby on 2006-07-09
Also, you can find a lot of themes / color schemes / etc for KDE [here.]("http://www.kde-look.org")

---

### Post by tcollogne on 2006-07-09
I noticed that kde uses different apps that gnome,

So if I install kde on top of ubuntu, does that give problems with the applications? I mean that there will be applications that do the same thing. Will they interfere with each other?

I have tried installing kubuntu, but I ran into some problems because I am new at linux and I use this guide

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

to get me started, but a whole bunch of things are different on kubuntu. For example the package manager, or installing j2re for firefox and so on.

Is there also some sort of guide for kubuntu?

---

### Post by tcollogne on 2006-07-09
To clarify. The problem is that I like the kde desktop more, but I find the extra apps (nautilus, synaptec package manager,...) on gnome more easy to use.

So I would like to have the kde desktop with the gnome apps. If I install kubuntu, I have all the other kde apps which I don't want.

Is it possible to install the kde desktop on ubuntu, but without all the extra apps like konqueror?

---

### Post by aysiu on 2006-07-09
Konqueror is not an extra app. It is as essential to KDE as Nautilus is to Gnome. You don't have to *use* Konqueror, but no matter how minimal a KDE install you do, Konqueror will always be there.

Try this: ```
sudo aptitude update
sudo aptitude install kdebase
``` If that's *too* minimal, try ```
sudo aptitude update
sudo aptitude install kde-core
```

---

### Post by tcollogne on 2006-07-10
Thanks. I did not know that. I will try with kdebase/kde-core.

---

