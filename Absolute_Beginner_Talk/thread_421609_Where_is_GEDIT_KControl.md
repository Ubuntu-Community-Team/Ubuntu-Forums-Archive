---
title: "Where is GEDIT? KControl?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by johnbick on 2007-04-24
NEWBIE Warning: I am new to Linux having not touched a Unix system since back in the 70s.... I am quite familiar with Windows and other systems and thought it was time to "get with it and become familiar with Linux. This seemed like an excellent place to start!

I have installed Kubuntu as the sole system on an IBM T40 laptop. There are several things I would like to tailor based on suggestions seem in other areas/forums. This has led to two very basic questions: 

A: Many tailoring suggestions involve using GEDIT. But when I fire up the Konsole and try to run --> sudo gedit ..... I get the message "sudo: gedit: command not found".

B: I have similarly seen references to using KControl to make some other changes -- but I do not find it in my Kubuntu installation.

Where might these be hiding? I thought both were part of the standard installation. (My system installed with no errors and I did check the disk integrity before installation!) If I need to install them from another location a pointer would be appreciated... Thanks in advance

---

### Post by taurus on 2007-04-24
Gedit is for Gnome.  Since you are running KDE, you need to use kate.

```
kdesu kate filename
```

---

### Post by ggaaron on 2007-04-24
Prior using, you must install gedit:
```

sudo apt-get install gedit

```
or you can use KDE tools - like kwrite, kate

Don't capitalize, use
```

kcontrol

```
not KControl.

Hope it helps.

Aaron.

---

