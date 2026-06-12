---
title: "Completely removing KDE"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Johnny K on 2007-06-21
I was gonna go with "Kompletely removing KDE", but...

Anyway, I installed KDE just to give it a try. I used the instructions on [this page]("http://www.psychocats.net/ubuntu/kde"), which tells you to do
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```
So I did it, tried it out, and then went back to GNOME. Then I tried to remove KDE via
```
sudo aptitude remove kubuntu-desktop
```
but some KDE applications still remain, Konqueror, Konsole, and Kamera for example. I know how to remove these individually, but how do I make sure I remove all remnants of KDE?

---

### Post by Clay_Banger on 2007-06-21
try the remove kubuntu part on this page:
[http://psychocats.net/ubuntu/puregnome]("http://psychocats.net/ubuntu/puregnome")

---

### Post by Inxsible on 2007-06-21
if you used aptitude to install it,doing a 
```
sudo aptitude remove kubuntu-desktop
``` should remove everything. Are you sure the applications are still there and not just the shortcuts ?

---

### Post by Johnny K on 2007-06-21
Doing
```
sudo aptitude remove kubuntu-desktop
```
still leaves the applications I mentioned before (konsole, etc)

If I go into synaptic and type "kde" it lists all the KDE stuff I have installed. But how do I know which packages were there from the beginning and which packages were installed with kubuntu-desktop?

---

### Post by alienexplorers on 2007-06-21
Your best bet is to go to this page and run the commands listed.
> [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

