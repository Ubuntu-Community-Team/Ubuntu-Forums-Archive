---
title: "Can I use K-whatever"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by SirGrant on 2007-04-30
I was under the impression that I can't use programs like kopote or anything basically that is ment for KDE because I'm running gnome.  Is this the case or can I run KDE programs under ubuntu?

---

### Post by Seisen on 2007-04-30
A lot of times you have to actually install KDE with the packages, sometimes you don't. Try installing kopete and see what else it trys to install. I use quanta and it only install a few KDE apps in Gnome.

---

### Post by walesmd on 2007-04-30
In my experience, if you attempt to install a KDE app the package manager will download an dependencies you need. KDE and Gnome tend to get along with one another to a reasonable extent - I have not run into any instances with the leading KDE apps where they would not run under Gnome (although there may be slight changes in the programs behavior - click and drag might do something different [move, rather than copy] for instance.

Best advise: just try it - if it doesn't work, find a Gnome equivalent. :D

---

### Post by Lord Illidan on 2007-04-30
> **SirGrant said:**
> I was under the impression that I can't use programs like kopote or anything basically that is ment for KDE because I'm running gnome.  Is this the case or can I run KDE programs under ubuntu?

You can run KDE programs under GNOME and vice-versa with no problems. The apps will look a little different from the styling, as the widgets are using different toolkits (GTK and QT).

All you have to do is install the libraries required, which in Ubuntu/Kubuntu's case can be handled with apt-get/aptitude/synaptic very well. Just type sudo aptitude install kopete for example.

---

### Post by Nythain on 2007-04-30
yeah, you can run kde apps in gnome, and gnome apps in kde... on slower machines you might notice a performance drop since it has to load important libraries from the other de to do it, like a lot of kde apps will rely on qt libraries and gnome apps on gtk libraries, but it will work, and on a decent machine it will work well... like mentioned they will look out of place cause they use different window manager engines or some junk like that

---

