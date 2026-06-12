---
title: "Kubuntu from Ubuntu"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-04-21
Can I / how do I convert to Kubuntu without a complete reinstall?

I've installed KDE on top of Ubuntu but now half my windows look like GNOME and the other half like KDE, that and there's loads of double options in all my menus, no doubt wasting a lot of disk space.

---

### Post by bobplano on 2007-04-21
sudo apt-get remove gnome-desktop gets rid of gnome and all the gnome apps

---

### Post by SOULRiDER on 2007-04-21
I suggest you do:

```
sudo aptitude install kubuntu-desktop

sudo aptitude remove ubuntu-desktop
```

---

### Post by bobplano on 2007-04-21
> **SOULRiDER said:**
> I suggest you do:

```
sudo aptitude install kubuntu-desktop

sudo aptitude remove ubuntu-desktop
```

yes. aptitude does a better job of getting rid of unused dependencies than apt-get

---

### Post by DSn0wMan on 2007-04-21
I would take a look here: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

While you could just add and remove desktops you might find that you need to do more. For instance if you are going to run KDE you might want to also switch to the KDM from the GDM.

---

### Post by cypherzero on 2007-04-21
*sudo aptitude install kubuntu-desktop* worked but *sudo aptitude remove ubuntu-desktop *doesn't seem to have removed much.
GNOME and all it's applications are still there, and as a side effect all the KDE text is really huge.

---

### Post by bobplano on 2007-04-21
> **cypherzero said:**
> *sudo aptitude install kubuntu-desktop* worked but *sudo aptitude remove ubuntu-desktop *doesn't seem to have removed much.
GNOME and all it's applications are still there, and as a side effect all the KDE text is really huge.

sorry i didn't read the commands the correct command is 
```
sudo aptitude remove gnome-desktop
```

---

### Post by cypherzero on 2007-04-21
*sudo aptitude remove gnome-desktop* tells me there's no such package!

---

### Post by bobplano on 2007-04-21
try sudo apt-get remove ubuntu-desktop. aptitude is better for something like this but if it doesn't work and this doesn't work just remove it using synaptic

---

### Post by SOULRiDER on 2007-04-22
Yeah, you might need to manually eliminate all packages you dont want.

---

### Post by medad on 2007-04-22
Sometimes it is just better to start from scratch.  That way you can set up the system exactly the way you want it.](*,)

---

