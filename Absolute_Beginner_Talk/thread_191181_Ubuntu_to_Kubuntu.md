---
title: "Ubuntu to Kubuntu"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-06-07
I would like to change ubuntu to kubuntu, or just replace gnome with KDE.. how to do that? :)

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=J-Gaming]I would like to change ubuntu to kubuntu, or just replace gnome with KDE.. how to do that? :)[/QUOTE]
Just run the following command in terminal.
> sudo apt-get install kde

It will install alot of packages and then when it's done logout. Under sessions you should see "kde." Select it and make it your default Desktop Enviroment. If you don't like KDE, just switch back to Gnome by loggin out and selecting it.

---

### Post by ajgreeny on 2006-06-07
Rather than install kde look for *kubuntu-desktop* in synaptic, or just use apt-get install as masterchief suggested.  A lot of the packages will be the same but kubuntu-desktop will give you the appropriate splash screens and other branding for kubuntu as well.

I did this first when using breezy back in Sept 05 and have done it again in Dapper without any difficulties.  Give it a try!

---

### Post by xtacocorex on 2006-06-07
I would recommend to do this:
```
sudo aptitude install kubuntu-desktop
```
instead of
```
sudo apt-get install kubuntu-desktop
```
as it's easier to remove all of Kubuntu if you want to in the future.

If you don't care about not removing it in the future, go with the second option, as MasterChief1234 stated above.

---

### Post by SynapseR on 2006-06-07
If I may ask, what is the difference between aptitude and apt-get ?

---

### Post by xtacocorex on 2006-06-07
They both do the same thing, but aptitude keeps track of the actual packages in the meta-package and will uninstall them if you uninstall the meta-package, whereas apt-get will only uninstall the meta-package only.

---

### Post by impakt on 2006-06-07
what is the advatage of KDE over gnome? disadvantages? any other reason i should switch?

---

### Post by aysiu on 2006-06-07
Differences and similarities:
[http://www.psychocats.net/ubuntu/kdevsgnome](http://www.psychocats.net/ubuntu/kdevsgnome)

Add Ubuntu:
[http://www.psychocats.net/ubuntu/gnome.html](http://www.psychocats.net/ubuntu/gnome.html)

Get rid of Kubuntu:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

