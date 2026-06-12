---
title: "Diffrences in Linux platforms"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by zanazzi on 2007-07-06
A point was made in another thread that it is better to stick to running Gtk apps in Gnome.

This seems intuitive but since i found that Katapult runs fine in Gusty, it raised the question as to what are the fundamental differences in the platforms, i.e. whats the difference between KDE and Gnome? and how come applications can cross platforms?

This may seem like a silly question but i don't know the answer and it would be nice to be told, im sure there are other people out there new to linux who may benefit from knowing to.

thank you for your time and advice

---

### Post by p_quarles on 2007-07-06
The main difference, as I understand it, is that GNOME and KDE each have their own set of libraries. If you have both libraries installed (which you will, if you use a package manager that fetches dependencies), most applications will run in either environment. Some applications won't work because they conflict directly with another one (these are mostly basic services). Others won't do everything they're designed to do. For instance, if you install Konqueror in GNOME, it won't automatically set itself up as your file manager.

---

### Post by zanazzi on 2007-07-06
So how did Gnome and kde developed independantly? 

why have 2 sets of conflicting libraries?

Doesn't it make things more complicated?

---

### Post by p_quarles on 2007-07-06
They're both built on top of the X windowing system, but apart from that, yes, they're pretty independent. KDE was not originally a completely open project (but is now, I believe), but GNOME has always been part of the GNU project. GNU, from the beginning, wanted to be able to ensure that it's projects were free from any proprietary claims, so has always written it's software from the ground up. 

The libraries aren't conflicting, though, they're just separate. Installing both won't give you any problems, unless you have limited storage space. Personally, I think it just gives the end-user more options and flexibility.

---

### Post by az on 2007-07-06
> **p_quarles said:**
> They're both built on top of the X windowing system, but apart from that, yes, they're pretty independent. KDE was not originally a completely open project (but is now, I believe), but GNOME has always been part of the GNU project. GNU, from the beginning, wanted to be able to ensure that it's projects were free from any proprietary claims, so has always written it's software from the ground up. 

The libraries aren't conflicting, though, they're just separate. Installing both won't give you any problems, unless you have limited storage space. Personally, I think it just gives the end-user more options and flexibility.

KDE is built using the QT toolkit, which was non-free at the very beginning.  KDE had a more advances Desktop Environment at the very beginning.  The QT librabries are still dual-licenced today.

Gnome was built on top the the GTK toolkit.  It has always been only licenced under the GPL.  A few years ago, lots of KDE developers felt that KDE was dissorganised and uninnovative.  At the same time, Gnome developers set a few guidelines for human interfaces and focused on making a lean and innovative desktop environment.  

There are a number of projects which oversee the integration or standards-compliance of desktop environments so that you can run apps from one DE on another DE.

---

### Post by PcFrk256 on 2007-07-06
KDE and Gnome are just different GUIs. Each have their own pros and cons. In my experience, KDE is more user friendly and has more of a Windows feel but is also a little slower in my uses. Gnome is more professional looking and a little more difficult to use- Gnome is good for servers. It all boils down to preference, and if you haven't seen either of them, do a Google Image search to look at screenshots. 

As far as Linux distros go, each one is good for something difference. RedHat, Ubuntu Server, and SUSE Enterprise are great for running a Linux based server. Knoppix(full install), Kanotix(full install), and Ubuntu Desktop are good for your typical setup. Again, it's all preference and based on what you need. Kanotix is my favorite for home. SUSE Enterprise and Ubuntu Server(with GNOME) are good for servers.

---

### Post by p_quarles on 2007-07-06
> Gnome is good for servers.

For a small home network, maybe, but for any server getting heavy use you wouldn't want a GUI at all. Gnome's primary intent is for desktops and workstations.

---

