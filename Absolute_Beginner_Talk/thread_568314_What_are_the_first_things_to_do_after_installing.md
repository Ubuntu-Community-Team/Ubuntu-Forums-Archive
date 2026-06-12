---
title: "What are the first things to do after installing?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by sheikyerbouti on 2007-10-05
On Mac OSX, there is a bunch of stuff I do right away or tell people to do right away, install flipformac, get vlc player, etc. I just installed xubuntu on one of my machines and I want to know what I should do first. So far I have installed skype, pidgin and mplayer. Any other killer apps or plug ins I should get?

Side question, How do I right click with a one button mac mouse. It's not a macintosh computer if that matters.

Another question: How do I add a little icon/launcher on the top bar across the screen. Firefox has one by default. How do I add more up there?

---

### Post by Pumalite on 2007-10-05
Do updates
sudo apt-get install build-essential
sudo apt-get install ubuntu-restricted-extras
You can install the rest (anything you want) via Synaptic
Don't miss k3b

---

### Post by sheikyerbouti on 2007-10-05
> **Pumalite said:**
> Do updates
sudo apt-get install build-essential
sudo apt-get install ubuntu-restricted-extras
You can install the rest (anything you want) via Synaptic
Don't miss k3b

Thanks. I ran those commands. What do they do? And what does "sudo apt-get" mean?

Also what is k3b?

---

### Post by skymera on 2007-10-05
K3b is a cd buring tool for KDE but can be used for Gnome.

apt-get is a package management tool.
from the repositories it download programsm libraries etc.

---

### Post by bobbocanfly on 2007-10-05
K3b = CD/DVD Burning package, a little bit like Nero

Apt-get is Ubuntus way of tracking what you have installed on your computer and helping you install or remove programs already on the computer. For example typing 

```
sudo apt-get install firefox
```

would install firefox and

```
sudo apt-get remove firefox
```

would remove it. The Sudo prefix means run he next command as the root (admin) user. You need to run apt-get as Root or it wont work.

Not every app is in apt-get but a whole load of them are.

---

### Post by Pumalite on 2007-10-05
Buid-essential is a package that install headers, gcc, compilers, etc. It allows you later to compile modules into your kernel such as graphic drivers, etc.

---

### Post by mgmiller on 2007-10-05
> Another question: How do I add a little icon/launcher on the top bar across the screen. Firefox has one by default. How do I add more up there?

You can drag and drop items there from your Applications menu.

Or you can go into the Appications menu and select an item and right click it and select "Add to Panel"

Or you can right click a blank area on the panel and select 'Add to panel"  This will show you a lot of things that you can add.

Or you can create a new launcher with any command and put it in the top or bottom panel.

I don't know how to right click with a 1 button mac mouse.  "normal" mice are very cheap.  Did you know a Microsoft USB intellimouse explorer will work perfectly in MAC and all the buttons will be recognized instantly?  It also works great in Ubuntu.  Although I think you said the computer you are using is not a MAC.  It doesn't matter, just get a 2 (or 3 or more) button mouse. Cheap, easy, right click is useful and even the center button is very useful in Linux for copy paste operations.

---

### Post by funrider on 2007-10-05
1. make sure flash can be loaded in broswer
2. make sure video player play my video file
3. check if there be any update from the update manager
4. make sure all hardware works well (especially if you use laptop)
5. get k3b as dvd burner
6. what's next?

---

### Post by Shazaam on 2007-10-05
humor on--

Tweak it till it breaks!

humor off--


:lolflag:

---

