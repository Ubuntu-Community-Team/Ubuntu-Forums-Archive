---
title: "Different software for KDE and GNOME?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2007-05-02
I'm installing kubuntu-desktop from Synaptic as we speak.  I noticed one of the packages discussed on the help files and one of the ones Synaptic listed was Open Office.  Does this mean that Gnome and KDE will have to have different versions of the same software?

What I'm asking is: if I have a program installed on my computer will it work on GNOME and KDE, or do I have to install the program on both desktops separately.


Also is it easy to uninstall the KDE enviornment and all those packages if I decide to get rid of it?

PS: thanks for being SO helpful these last few days!

---

### Post by aysiu on 2007-05-02
All programs will work on both Gnome and KDE.

If you want to get rid of KDE, read this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by igknighted on 2007-05-02
> **JacobRogers said:**
> I'm installing kubuntu-desktop from Synaptic as we speak.  I noticed one of the packages discussed on the help files and one of the ones Synaptic listed was Open Office.  Does this mean that Gnome and KDE will have to have different versions of the same software?

What I'm asking is: if I have a program installed on my computer will it work on GNOME and KDE, or do I have to install the program on both desktops separately.


Also is it easy to uninstall the KDE enviornment and all those packages if I decide to get rid of it?

PS: thanks for being SO helpful these last few days!

1) Apt should take care of all dependencies.  Some times you need a kde-bindings to let a program talk to some of the kde specific subsystems (like arts).  There are also other apps that are KDE native that you should use instead of the gnome version while in KDE (kate/kwrite instead of gedit, konqueror instead of FF or Nautilus, etc.).  All Gnome apps can be used in KDE tho if you prefer and vice-versa.

2) sudo apt-get remove kubuntu-desktop && sudo apt-get autoremove

OR if you installed via aptitude

sudo aptitude remove kubuntu-desktop && sudo apt-get autoremove

---

### Post by aysiu on 2007-05-02
> **igknighted said:**
> 
OR if you installed via aptitude

sudo aptitude remove kubuntu-desktop && sudo apt-get autoremove Theoretically, if you installed using *aptitude*, you shouldn't need the second part of that command.

---

### Post by igknighted on 2007-05-02
> **aysiu said:**
> Theoretically, if you installed using *aptitude*, you shouldn't need the second part of that command.

Yeah, but I have had a few times were aptitude left a few things that autoremove was needed to clean out, so I thought I'd add it for completeness.

---

### Post by aysiu on 2007-05-02
> **igknighted said:**
> Yeah, but I have had a few times were aptitude left a few things that autoremove was needed to clean out, so I thought I'd add it for completeness.
Cool.

---

### Post by JacobRogers on 2007-05-02
Does this mean that I'm downloading a redundent copy of Open Office?

Is everything going to be ok?

---

### Post by igknighted on 2007-05-02
> **JacobRogers said:**
> Does this mean that I'm downloading a redundent copy of Open Office?

Is everything going to be ok?

Nope, its probably just an interface layer.  Also, it could be an updated version replacing your current one (would have happened in the next update anyway if this is what it is).

---

### Post by aysiu on 2007-05-02
> **JacobRogers said:**
> Does this mean that I'm downloading a redundent copy of Open Office?

Is everything going to be ok?
Everything's going to be fine. You're probably downloading some package that gives you better KDE integration for OpenOffice. You're not redownloading the entire OpenOffice.

---

### Post by JacobRogers on 2007-05-02
Ok neat.  I'll make sure to tell you of my success using KDE, hopefully right fro Konqueror.

---

### Post by JacobRogers on 2007-05-02
Installing KDE was very easy!   I'm in KDE right now It changed the splash screen I see when I boot up and shut down and I'm not sure how I feel about that.  I liked the ubuntu logo and colors.

It's been a good while since I used KDE, and I forgot how Windows-ish it looks.

---

### Post by aysiu on 2007-05-02
> **JacobRogers said:**
> Installing KDE was very easy!   I'm in KDE right now It changed the splash screen I see when I boot up and shut down and I'm not sure how I feel about that.  I liked the ubuntu logo and colors. That can be fixed:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

> 
It's been a good while since I used KDE, and I forgot how Windows-ish it looks. That can be fixed to. Just play around with the settings:
[http://www.kde-look.org](http://www.kde-look.org)

---

