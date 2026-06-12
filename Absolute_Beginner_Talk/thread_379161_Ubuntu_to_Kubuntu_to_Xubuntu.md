---
title: "Ubuntu to Kubuntu to Xubuntu"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-03-08
If I want to have KDE in place of GNome, or switch from one to other, how do I do it without installing the complete packages ? And will the switchings affect the running of any of my programs ?

---

### Post by etank on 2007-03-08
You can do a ```
sudo aptitude update
``` then ```
sudo aptitude install kubuntu-desktop
```
that will install the KDE desktop on your machine and will allow you to select a Gnome or KDE at login. Here is a good document that explains it a little more [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde).

---

### Post by steve101101 on 2007-03-08
then to switch the desktop environment click on the sessions button in the startup window.

---

### Post by x1a4 on 2007-03-08
Hi,

As a general rule try to stay away from those large meta packages.  Instead install *kde-core* and any other KDE packages you like.

---

### Post by Perfect Storm on 2007-03-08
> **x1a4 said:**
> Hi,

As a general rule try to stay away from those large meta packages.  Instead install *kde-core* and any other KDE packages you like.

I wouldn't say that. The Meta packages is great if you're new and want it all ready to be used with a nice theme and setup.

---

