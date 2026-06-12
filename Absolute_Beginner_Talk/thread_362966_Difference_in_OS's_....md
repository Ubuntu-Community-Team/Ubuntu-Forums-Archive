---
title: "Difference in OS's ... ?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-02-16
What exactly is the difference between Ubuntu, Kubuntu, and Fluxbox.  I have read a lot on Kubuntu, but I cannot tell the real difference beside the user interface.  All tips much appreciated, thank you :)

---

### Post by ComplexNumber on 2007-02-16
ubuntu uses a desktop environment called gnome. kubuntu uses a desktop environement called kde. each desktop environment tends to have several 'components' - a window manger(it controls the placement and appearance etc of the windows for each application), a set of libraries, a toolkit(this determines the apparence and gives it its look and feel), a panel, various appications which use the desktop environments toolkit, etc. 
as a bare minimum, you can have just a window manager. fluxbox is a window manager. kde has kwin as its window manager, and gnome has metacity.

thats a simplified version anyway :p

---

### Post by 3rr0r on 2007-02-16
> **ComplexNumber said:**
> ubuntu uses a desktop environment called gnome. kubuntu uses a desktop environement called kde. each desktop environment tends to have several 'components' - a window manger(it controls the placement and appearance etc of the windows for each application), a set of libraries, a toolkit(this determines the apparence and gives it its look and feel), a panel, various appications which use the desktop environments toolkit, etc. 
as a bare minimum, you can have just a window manager. fluxbox is a window manager. kde has kwin as its window manager, and gnome has metacity.

thats a simplified version anyway :p

SO besides the user interface, how it looks, are there any differences in what they actually do or how they work ?

---

### Post by igknighted on 2007-02-16
> **3rr0r said:**
> SO besides the user interface, how it looks, are there any differences in what they actually do or how they work ?

Not really, there are different programs in some cases (kate/kwrite as text editors in KDE, gedit in gnome... k3b for burning in KDE, gnomebaker in gnome... etc), but the basic OS is the same, just different graphical interface on top.

---

### Post by Bachstelze on 2007-02-16
It is worth noting, though, that applications designed for KDE (e.g. k3b or Amarok) will work in Gnome too - and vice versa -, and also that you can very well have KDE and Gnome installed, choosing which one you want to start when you login.

---

### Post by ComplexNumber on 2007-02-16
> **3rr0r said:**
> SO besides the user interface, how it looks, are there any differences in what they actually do or how they work ?
no. as other posters have said, they(ie the desktop environments such as gnome and kde) are just different 'flavours'.  
NOTE: fluxbox is not a desktop enviroment. it is a window manager. it doesn't have the extra functionality that a desktop enviroment gives.however, there is nothing wrong with installing a whole desktop enviroment, but running fluxbox on top of that as your main window manager. 

here are several practical scenarios:
a) install everything from both kde and gnome,  yet use gnome as your main desktop environment. this will mean that you can also have access to the kde  libraries so that you can run kde applications. this also means that you can select either gnome or kde as your main desktop environment at the login screen.
b) install everything from both kde and gnome,  yet use kde as your main desktop environment. this will mean that you can also have access to the gnome  libraries so that you can run gnome applications. this also means that you can select either gnome or kde as your main desktop environment at the login screen.
c) install all of gnome and only the libraries of kde. this means that you will only have the choice as gnome as a desktop enviroment, but it also allows you to use kde applications.
c) install all of gnome and only the libraries of kde and kde's toolkit(ie qt). this means that you will only have the choice as gnome as a desktop enviroment, but it also allows you to use kde applications.
d) install all of kde and only the libraries of gnome and gnome's toolkit(ie gtk). this means that you will only have the choice as kde as a desktop enviroment, but it also allows you to use gnome applications.
e) install of gnome, qt on its own, and none of kde. same as c, but you can only run qt applications that don't depend upon kde's libraries. as example being qtdesigner.
f) install of kde, gtk on its own, and none of gnome. same as d, but you can only run gtk applications that don't depend upon gnomes's libraries. as example being alsaplayer.
g) install fluxbox, barest gtk, barest qt, none of gnome, and none of kde. this will be very bare - just fluxbox and applications that don't depend upon gnome or kde libraries, but you will be able to run applications that use the gtk or qt toolkit, but that don't depend on either kde or gnome

NOTE: kde's toolkit is qt. gnome's toolkit is gtk.

---

### Post by 3rr0r on 2007-02-16
> **ComplexNumber said:**
> no. as other posters have said, they(ie the desktop environments such as gnome and kde) are just different 'flavours'.  
NOTE: fluxbox is not a desktop enviroment. it is a window manager. it doesn't have the extra functionality that a desktop enviroment gives.however, there is nothing wrong with installing a whole desktop enviroment, but running fluxbox on top of that as your main window manager. 

here are several practical scenarios:
a) install everything from both kde and gnome,  yet use gnome as your main desktop environment. this will mean that you can also have access to the kde  libraries so that you can run kde applications. this also means that you can select either gnome or kde as your main desktop environment at the login screen.
b) install everything from both kde and gnome,  yet use kde as your main desktop environment. this will mean that you can also have access to the gnome  libraries so that you can run gnome applications. this also means that you can select either gnome or kde as your main desktop environment at the login screen.
c) install all of gnome and only the libraries of kde. this means that you will only have the choice as gnome as a desktop enviroment, but it also allows you to use kde applications.
c) install all of gnome and only the libraries of kde and kde's toolkit(ie qt). this means that you will only have the choice as gnome as a desktop enviroment, but it also allows you to use kde applications.
d) install all of kde and only the libraries of gnome and gnome's toolkit(ie gtk). this means that you will only have the choice as kde as a desktop enviroment, but it also allows you to use gnome applications.
e) install of gnome, qt on its own, and none of kde. same as c, but you can only run qt applications that don't depend upon kde's libraries. as example being qtdesigner.
f) install of kde, gtk on its own, and none of gnome. same as d, but you can only run gtk applications that don't depend upon gnomes's libraries. as example being alsaplayer.
g) install fluxbox, barest gtk, barest qt, none of gnome, and none of kde. this will be very bare - just fluxbox and applications that don't depend upon gnome or kde libraries, but you will be able to run applications that use the gtk or qt toolkit, but that don't depend on either kde or gnome

NOTE: kde's toolkit is qt. gnome's toolkit is gtk.


I was thinking of using fluxbox, but only because every ss I have seen is very minimalist.  I'm not sure if I quite understand its funciton as solely a windows manager.  How does that differ from the "normal" desktop environment.  My only perception of fluxbox is a link to a ss one of the mod's has set up.  THe mod with the eye avatar, I believe.

---

### Post by igknighted on 2007-02-16
> **3rr0r said:**
> I was thinking of using fluxbox, but only because every ss I have seen is very minimalist.  I'm not sure if I quite understand its funciton as solely a windows manager.  How does that differ from the "normal" desktop environment.  My only perception of fluxbox is a link to a ss one of the mod's has set up.  THe mod with the eye avatar, I believe.

I would recommend ICE WM over fluxbox, both are minimal but ice is easier to set up.  Either way, you could install both and play around.  There is a fluxbuntu that installs fluxbox as its default wm, but i don't know how to get it.

---

