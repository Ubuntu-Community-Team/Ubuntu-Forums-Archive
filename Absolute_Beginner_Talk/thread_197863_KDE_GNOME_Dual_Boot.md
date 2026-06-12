---
title: "KDE GNOME Dual Boot"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Chmoore on 2006-06-16
Last year I installed Ubuntu 5.10 with the default Gnome desktop.  

Then a came across a KDE add-on I installed that on every Ubuntu startup gave me a choice of running either KDE or Gnome.

I'm currently running the latest Ubuntu with Gnome.  

I'd like to run that same setup I had last year with 5.10.  That is, I'd like to have a choice of running either KDE or Gnome whenever the Ubuntu login page comes up.

Does anyone know where I can find the KDE add-on that offers the choice of running KDE or Gnome?

Thanks,

- Chmoore

---

### Post by raptros-v76 on 2006-06-16
if you install kubuntu, gdm (or kdm if you choose to use that) will allow you to choose the session you want to log into, giving you the option of a gnome or kde session. its all very well thought out

---

### Post by pyromithrandir on 2006-06-16
sudo apt-get install kubuntu-desktop

---

### Post by Chmoore on 2006-06-16
That's it.  Got it loaded.  Works great.  

Thanks for the help.

Chmoore

---

### Post by aysiu on 2006-06-16
*apt-get* works great until you try to do ```
sudo apt-get remove kubuntu-desktop
``` and then realize it does essentially nothing.

In the future, please recommend this command instead: ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

### Post by bruce89 on 2006-06-16
I'd use aptitude for everything actually.

---

### Post by aysiu on 2006-06-16
[QUOTE=bruce89]I'd use aptitude for everything actually.[/QUOTE]
So do I, but it's especially important for these metapackages.

---

### Post by Nibiruet on 2006-06-16
[QUOTE=aysiu]*apt-get* works great until you try to do ```
sudo apt-get remove kubuntu-desktop
``` and then realize it does essentially nothing.

In the future, please recommend this command instead: ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```[/QUOTE]
Asuume reverse would be:

sudo aptitude remove kubuntu-desktop  ?

---

### Post by aysiu on 2006-06-16
[QUOTE=Nibiruet]Asuume reverse would be:

sudo aptitude remove kubuntu-desktop  ?[/QUOTE]
Yes, but that will work only if you use the recommended command to install Kubuntu.

If you do ```
sudo aptitude remove kubuntu-desktop
``` after installing it with *apt-get*, it won't make a difference. It needs to be installed with *aptitude*, and it needs the update.

It's not enough to just do ```
sudo aptitude install kubuntu-desktop
``` You have to do ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` to be able to remove it properly with *aptitude*.

---

### Post by user1397 on 2006-06-16
how do you have patience with this subject, aysiu?  it seems like everyday you have to give out this aptitude advice at least 5 times!! :p

---

### Post by aysiu on 2006-06-16
*apt-get* is deeply entrenched in people's vocabulary--*aptitude* is not. It takes a lot of time and patience to get people into *aptitude*.

I won't force *aptitude* on people for everyday stuff, but for desktop environment metapackages, it's a must.

---

