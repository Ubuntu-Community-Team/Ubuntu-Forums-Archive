---
title: "What ARE the different parts--and how do they work together?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2006-11-17
I've been enjoying learning about/using Ubuntu for three months now or so, and I'm curious to understand more about the various parts that make up this new critter...

There are lots of new terms--GTK, X, Nautilus, KDE, gnome, Kernel, etc--but I don't really understand what their respective functions are and how they fit together...   

The 'kernel' is the basic, fundamental OS part of Linux, if I understand correctly, but all of the other "parts" work on top of that.

What would really help is a good analogy--or even better (since I tend to think visually)--would be a nice graphic that shows what the different pieces are and how they are related/connected to each other.

Does anyone know if this kind of thing exists in one place?  Is there a good primer somewhere that would explain the parts that make up the whole?

I *could* hunt down each piece separately, I suppose, but it would be much more *fun* to have someone tie it all together for me!   (Nuthin' makes learnin' fun like a good teacher!) ;)

---

### Post by Kurt` on 2006-11-17
X, Xorg, X11 = the "X Windows" system. Think of it as a intermediary layer between the kernel and your monitor. It allows Window Managers such as KDE and Gnome to access your video hardware easily.

KDE and Gnome are Window Managers. Think of them like the Microsoft Windows interface. It's a system that manages all your running GUI applications, provides you with easy access to different functions ("Start Menu"), and graphical tools for configuring your system.

GTK = The GIMP ToolKit. It's basically a set of libraries than an application can use to create/display windows and other things. Many apps use GTK+, such as The GIMP itself. The KDE equivalent is QT.

Nautilus is basically your Linux equivalent of "Windows Explorer". It allows you to browse and manipulate files graphically within GNOME.

---

### Post by smoker on 2006-11-17
great explanation, Kurt'

enlightened me about a lot of stuff!

cheers :-)

---

