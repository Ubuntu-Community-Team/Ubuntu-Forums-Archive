---
title: "What's the kio-uiserver?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bw44 on 2008-02-18
I've installed the home accounting package Eqonomize! which was developed under KDE but runs pretty well under Gnome.  

Whenever I've made changes to any of my Eqonomize accounts and quit the program, a task appears in the lower panel which says kio-uiserver.  It seems to hang around for several seconds and then vanishes.

I Googled "kio-uiserver" but couldn't find a layman's description of what it is.   I assume it's benign,but can anyone tell me what it is and what it might be doing in this case?

Thanks.

---

### Post by randy78 on 2008-02-18
It's probably just waiting for all instances of the program to close before it exits...

---

### Post by bw44 on 2008-02-18
> **randy78 said:**
> It's probably just waiting for all instances of the program to close before it exits...

Thanks, but I'm still not understanding.  The kio-uiserver isn't running when the application is (at least there's no separate visible task in the panel) but Eqonomize is far and away the slowest application to quit. I assume because the kio-uiserver thing does have to run.  But why would it start up just to wait for Eqonomize to close?  It doesn't seem run  to after any other application I use.

Could anyone possibly shed any more light on what the kio-uiserver's  function is?

---

### Post by bw44 on 2008-02-20
Bump.

---

### Post by bw44 on 2008-02-22
Bump.  (I guess this is not a pressing issue for most newbies!) :)

---

### Post by fallen seraph on 2008-02-23
Well I'll add my voice as a newb who's quite curious and confused as to what this thing is.

---

### Post by bw44 on 2008-02-25
> **fallen seraph said:**
> Well I'll add my voice as a newb who's quite curious and confused as to what this thing is.I guess there aren't a lot of KDE users reading the Ubuntu forums (Kubuntu not withstanding).  Here's a couple of things I learned from poking around with Google:

KIO - extensible network-transparent file access.

KIO (KDE Input/Output) is part of the KDE architecture. It provides access to files, web sites and other resources through a single consistent API. Applications, such as Konqueror which are written using this framework can operate on files stored on remote servers in exactly the same way as they operate on those stored locally. This allows for a file browser like Konqueror to both be a highly versatile and powerful file manager as well as a web browser. [from [http://en.wikipedia.org/wiki/KIO]](http://en.wikipedia.org/wiki/KIO])

The Eqonomize program stores its data as XML, and when you make changes to your data and save it, I think the kio-uiserver is invoked to handle the access to the XML files.  Mind you, this is only a guess.  I was hoping someone with expertise would respond.  No such luck.  I'd especially like to know why the process is so slow.  It's not a good advertisement for the KDE interface, but maybe that's only because it's running under Gnome.

---

### Post by st1100pilot on 2008-03-26
I think it may have something to do with Amarok. I am running Gnome, but go that message this morning at the bottom of the screen when running Amarok. I don't recall seeing it at any other time.

---

### Post by tubasoldier on 2008-03-26
It is the KDE user interface server. It runs whenever there is a program written with QT is running.

---

### Post by bw44 on 2008-03-26
> **tubasoldier said:**
> It is the KDE user interface server. It runs whenever there is a program written with QT is running.Thanks for the post!  (I'd given up getting an answer and unsubscribed from the thread!) 

What is QT? And was I completely off base with my previous post about it having something to do  with writing out modified XML files?

I'm curious because when I close Eqonomize! the kio server starts and runs for several seconds (5 maybe) which seems a long time to do what?

Thanks again.

---

### Post by tubasoldier on 2008-03-27
QT is the graphical api that KDE and it's applications are written in. 
Gnome is written in GTK.

A brief history,
KDE was written first using a proprietary api called QT which was later licensed under the GPL
Gnome was written in response to this using an open api called GTK.

Now both are open and licensed under the GPL.
Thus the basis for most of the KDE/Gnome wars.

---

### Post by bw44 on 2008-03-27
> **tubasoldier said:**
> QT is the graphical api that KDE and it's applications are written in. 
Gnome is written in GTK.

A brief history,
KDE was written first using a proprietary api called QT which was later licensed under the GPL
Gnome was written in response to this using an open api called GTK.

Now both are open and licensed under the GPL.
Thus the basis for most of the KDE/Gnome wars.Many thanks for the education!  

Is it possible that the reason the kio-uiserver makes a slow appearance when I close Eqonomize is because I'm running an application written for KDE, but under Gnome?  If I ran it under KDE (in native mode), I guess the server would always be active, no?

---

