---
title: "can i download all the same edubuntu software for ubuntu?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by alexlex on 2007-04-21
is all the software for edubuntu available for download with ubuntu?

my second question is can i download KDE to run on ubuntu or do need to install kubuntu all by itself?

---

### Post by aysiu on 2007-04-21
Yes, and yes.

```
sudo apt-get update && sudo apt-get install edubuntu-desktop kubuntu-desktop
``` That will give you a ton of software, including all the extra Edubuntu software and KDE.

More details on KDE specifically:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by alexlex on 2007-04-21
> **aysiu said:**
> Yes, and yes.

```
sudo apt-get update && sudo apt-get install edubuntu-desktop kubuntu-desktop
``` That will give you a ton of software, including all the extra Edubuntu software and KDE.

More details on KDE specifically:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

thanks alot for the responce. will i be able to run the edubuntu software in ubuntu or will i have to change sessions?

---

### Post by aysiu on 2007-04-21
> **alexlex said:**
> thanks alot for the responce. will i be able to run the edubuntu software in ubuntu or will i have to change sessions?
You can run any software from anywhere. You can run KDE software in Gnome and Gnome software in KDE. You can run KDE and Gnome software in XFCE or IceWM or Fluxbox.

Software may be "designed for" a particular environment, but it can be run from anywhere.

That said, Edubuntu isn't its own environment. It actually uses Gnome (same as vanilla Ubuntu), but just has a different set of default packages and artwork.

From [Edubuntu's FAQ](http://www.edubuntu.org/FAQ): >  What are the differences between Ubuntu and Edubuntu?

Take [the tour](http://www.edubuntu.org/screenshots) of Edubuntu. There are many school-related applications installed by default, including TuxPaint, TuxMath, and TuxTyping, among others.

---

