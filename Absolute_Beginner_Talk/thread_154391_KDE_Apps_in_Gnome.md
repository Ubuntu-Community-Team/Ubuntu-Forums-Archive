---
title: "KDE Apps in Gnome?"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by cleentrax on 2006-04-03
Overall I plan to use Gnome as my desktop environment rather than KDE, but there are several KDE apps that I would like to use. What are my options? Do I need to do a separate install of Kubuntu, or is there a way to run both Gnome and KDE apps at the same time?

I'm thinking especially of Rosegarden and Quanta, but there are others as well.

---

### Post by gabruo on 2006-04-03
Any Kde apps should run in ubuntu.  You simply select the ones you want from Synaptic and it will install any Kde specific dependencies they might have.

---

### Post by GameGod on 2006-04-03
There's nothing extra you have to do to run KDE apps while running GNOME, or vice-versa. :)

The main reason KDE and GNOME apps are different is because they use different "GUI toolkits" - KDE apps are based on QT, and GNOME apps are based on GTK. In simple language, all that means is that a KDE/QT app will look different than a GNOME/GTK app, that's all. :)

---

### Post by 3rdalbum on 2006-04-03
It's not quite that simple actually... some features of some GNOME programs won't work under KDE and vice-versa. For instance, on anything other than GNOME, File Roller won't let you view compressed/archived text files. (it expects to find gEdit, and when it doesn't, it just brings up an error).

But that's about as bad as it gets.

---

### Post by cleentrax on 2006-04-03
The reason I asked is that I installed Rosegarden from Synaptic, but I can't find it in any menu or folder on my system. So I assumed that it was because it was a KDE app. There must be another reason...

---

### Post by meborc on 2006-04-03
what do you get if you type

**rosegarden**

in the terminal? ... if there were no errors while installing, it should be there (not in the menu but in the box)... it is not in the menu probably cuz it looks for KDE menu... also, if you go to synaptic, do you see **rosegarden** package installed? ... if you do, then right-click and see if you can find out what files and where were installed... you are probably looking something like .bin ;)

---

### Post by Sweet on 2006-04-03
[QUOTE=meborc]what do you get if you type

**rosegarden**

in the terminal? ... if there were no errors while installing, it should be there (not in the menu but in the box)... it is not in the menu probably cuz it looks for KDE menu... also, if you go to synaptic, do you see **rosegarden** package installed? ... if you do, then right-click and see if you can find out what files and where were installed... you are probably looking something like .bin ;)[/QUOTE]


Yeah, try that and if it runs you can add it to the menu by running the "smeg" menu editor:
```
sudo smeg
``` :D

---

