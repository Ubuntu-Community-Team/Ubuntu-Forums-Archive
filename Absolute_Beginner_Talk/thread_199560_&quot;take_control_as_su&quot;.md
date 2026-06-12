---
title: "&quot;take control as su&quot;"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-19
how can I use folders in the "GUI" as super user ?
in the terminal I just hit su and give password
but how can I do that in the "GUI" ?

---

### Post by johnnymac on 2006-06-19
gksu is the tool for that...

Example:
    gksu nautilus

---

### Post by aysiu on 2006-06-19
*su* shouldn't work unless you did an expert install or enabled the root account.

For GUI super-user, press Alt-F2.

In the run dialogue, type ```
gksudo nautilus
``` for Gnome or ```
kdesu konqueror
``` for KDE.

---

### Post by FizDev on 2006-06-19
You can also use the "Run as a different user" in System Tools, if it's not there then simply
```
gksuexec
```
That way you can any application you want using any account

---

### Post by ZeusABJ on 2006-06-19
Heh, I just asked this. Maybe we should make a sticky on "most useful Ubuntu commands". I'm actually compiling a text document for my records, maybe I'll post it when I'm done.

:KS

---

### Post by MaximB on 2006-06-19
I forgot ubuntu 6.06
is it gnome ? or maybe...KDE ?
I mean by default
and what is the deffrence

---

### Post by aysiu on 2006-06-19
Ubuntu is Gnome
Kubuntu is KDE
Xubuntu is XFCE

The difference between Gnome and KDE is here (and it's not much, honestly, even though people get into big arguments about it): [http://www.psychocats.net/ubuntu/kdegnome.html](http://www.psychocats.net/ubuntu/kdegnome.html)

Honestly, in both, you click an application, and it launches. You move a file to the trash, and it's in the trash. You change the wallpaper, and it changes. For basic stuff, they're essentially the same.

---

### Post by MaximB on 2006-06-19
I like Gnome better then KDE..
KDE is like windows in some way..

but what about XFCE ???
were can I see what is it ?

---

### Post by aysiu on 2006-06-19
KDE is often accused of being "Windows-like," but usually for the wrong reasons--it defaults to one toolbar at the bottom instead of one of at the top and one at the bottom. It also, in Ubuntu, has a blue color scheme instead of a brown/orange one.

Those things don't matter, though, because they can be easily changed. KDE is actually not at all like Windows. It defaults to a single-click to open files. It allows you to have a Mac OS-like toolbar that includes the application menu (Gnome cannot do this). Its System Settings window looks a lot like Mac OS X's System Preferences. Gnome has nothing of the sort.

In any case, to see what XFCE looks like, go [here](http://images.google.com/images?q=xfce&svnum=100&hl=en&lr=lang_en&safe=off&sa=G&imgsz=xxlarge). XFCE is mainly for low-spec systems--128 MB of RAM or less.

---

### Post by nealklomp on 2006-06-19
[QUOTE=MAXDDARK]I like Gnome better then KDE..
KDE is like windows in some way..

but what about XFCE ???
were can I see what is it ?[/QUOTE]

Xfce, its not just for low end machines. 
I have a Dell Insp 6m, I've been running Gnome as my prime DE, with a brief look at KDE, for 6 months. I am currently scouting Xfce and I've got to say it is a performance GUI as much as anything.
```

sudo apt-get install xubuntu-desktop
```

This will give you two desktop to choose from.

---

### Post by fridayxiii on 2006-06-19
[QUOTE=ZeusABJ]Heh, I just asked this. Maybe we should make a sticky on "most useful Ubuntu commands". I'm actually compiling a text document for my records, maybe I'll post it when I'm done.

:KS[/QUOTE]

Great idea.  As a new Ubuntu user one of my "to do" list items is to find a reference for most commonly used/useful Linux commands.  If you compile (or find) one it would definitely be sticky-worthy.  =D>

---

