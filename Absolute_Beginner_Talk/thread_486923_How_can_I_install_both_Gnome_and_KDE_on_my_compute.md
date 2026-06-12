---
title: "How can I install both Gnome and KDE on my computer?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by lawentzel on 2007-06-28
I have Ubuntu installed on my computer.  (7.04)  I would like to also have KDE on it as well.  It was suggested to type in:

```
sudo apt-get install kbuntu-desktop
```

I was thinking just going into Sysaptic Package Manager and adding "kde-core".  Would both ways work?  Is one better then the other?  Anything I need to worry about?  Thank you all in advance for your help.

---

### Post by Rocket2DMn on 2007-06-28
I suggest just using apt-get for kubuntu-desktop, I've seen it work for different environments, including KDE and XFCE.  You can just select your session at the bottom left of the login screen, and set whatever you want to default.

---

### Post by r4ik on 2007-06-28
Try,

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Good luck !

---

### Post by dptxp on 2007-06-28
First Install Ubuntu.
I use kde-core in place of kubuntu-desktop.
I have not tried the later, what extra does it give ?

---

### Post by mac71 on 2007-06-28
Hi,
I have both installed on my machine. I opened a terminal and did this:

sudo aptitude update
sudo aptitude install kubuntu-desktop

This way all associated apps and libs are installed along with the desktop, but more importantly, aptitude remembers them all. So if you later decide to remove kubuntu, you can just do:

sudo aptitude update
sudo aptitude remove kubuntu-desktop 

and unlike apt-get or synaptic, aptitude will remove all associated apps and libs. 
Hope that helps :D

---

### Post by steveneddy on 2007-06-28
> **mac71 said:**
> Hi,
I have both installed on my machine. I opened a terminal and did this:

sudo aptitude update
sudo aptitude install kubuntu-desktop

This way all associated apps and libs are installed along with the desktop, but more importantly, aptitude remembers them all. So if you later decide to remove kubuntu, you can just do:

sudo aptitude update
sudo aptitude remove kubuntu-desktop 

and unlike apt-get or synaptic, aptitude will remove all associated apps and libs. 
Hope that helps :D

Yeah - what he said. I have gnome and Fluxbox on my laptop and like having a fast and slick DE as opposed to the fat but cool and jiggly desktop (Gnome with Compiz)

---

### Post by lawentzel on 2007-06-29
Ok, got Gnome, KDE and even the Xfce on there.  I will probably install the Fluxbox as well, just haven't yet.  So now for my next stupid question.

Can I change the desktop settings, icons and menus for each of the desktop types without messing up the other one?  For example, XFce has several icons on it's desktop that it got from Gnome, but also added their own which ended up duplicating some icons.  So can I delete them, and not worry about them effecting the other desktop?  Thanks.

Just an FYI I did end up using this command and it installed flawlessly.
```
sudo apt-get install kbuntu-desktop
sudo apt-get install xubuntu-desktop
```

---

### Post by mac71 on 2007-06-29
> **lawentzel said:**
> Ok, got Gnome, KDE and even the Xfce on there.  I will probably install the Fluxbox as well, just haven't yet.  So now for my next stupid question.

Can I change the desktop settings, icons and menus for each of the desktop types without messing up the other one?  For example, XFce has several icons on it's desktop that it got from Gnome, but also added their own which ended up duplicating some icons.  So can I delete them, and not worry about them effecting the other desktop?  Thanks.

Just an FYI I did end up using this command and it installed flawlessly.
```
sudo apt-get install kbuntu-desktop
sudo apt-get install xubuntu-desktop
```

Glad you're all sorted. Just remember, should you decide to remove them at a later date: apt-get will not remove all dependencies, only the package you tell it to remove.

---

### Post by RedSquirrel on 2007-06-30
> **mac71 said:**
> Just remember, should you decide to remove them at a later date: apt-get will not remove all dependencies, only the package you tell it to remove.

apt-get in edgy and feisty will remove dependencies if you use autoremove. 

```
sudo apt-get autoremove package_name
```See the man page:

```
man apt-get
```

---

### Post by mac71 on 2007-06-30
Didn't know that. That's something to remember, though I'm in the habit of using aptitude now.

---

