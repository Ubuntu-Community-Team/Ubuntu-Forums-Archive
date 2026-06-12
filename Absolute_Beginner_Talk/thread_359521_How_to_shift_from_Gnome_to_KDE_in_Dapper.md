---
title: "How to shift from Gnome to KDE in Dapper"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2007-02-12
How to shift from Gnome to KDE in Dapper?

---

### Post by Jussi01 on 2007-02-12
to install: Go to terminal, type

```
sudo apt-get install kubuntu-desktop
```

Then once its done, press ctrl-alt-backspace

Choose from list in the bottom left corner the session kde and log in..

---

### Post by xyz on 2007-02-12
You may want to take a look at [this link]("http://www.psychocats.net/ubuntu/"),too.
Look for:
> Playing Around
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

---

### Post by vivin_west on 2007-02-12
vivin@vivin-desktop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: language-selector-qt but it is not going to be installed
E: Broken packages
vivin@vivin-desktop:~$

?????

---

### Post by Jussi01 on 2007-02-12
Go to synaptic, and from the menu select fix broken packages

---

### Post by vivin_west on 2007-02-12
I did it but still I get the same messg

---

### Post by vivin_west on 2007-02-12
Depends: language-selector-qt but it is not going to be installed
Can anyone tell what it means.

---

### Post by xyz on 2007-02-13
You may want to try this:
[Language selector for kubuntu linux]("http://www.gnusolaris.org/archive/elatte-unstable/admin/language-selector-qt")
Also if you open Synaptic > Search > language-selector-qt > Right Click > Properties > Dependencies...you'll be able to see what "language-selector-qt" depends upon.

---

### Post by vivin_west on 2007-02-13
what is the command to fix broken packages?

---

### Post by xyz on 2007-02-14
> **vivin_west said:**
> what is the command to fix broken packages?

As Jussi01 wrote a couple of posts above...go System > Administration > Synaptic Package Manager -enter your password- > Edit -scroll all the way down to > Fix Broken Packages.

---

### Post by aysiu on 2007-02-14
Dependency problems usually stem from conflicting repositories.

**Step 1**
Get a fresh repositories list by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**
Install Kubuntu by pasting these commands into the terminal: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Full instructions (with screenshots) here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

