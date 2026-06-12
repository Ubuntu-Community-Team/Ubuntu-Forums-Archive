---
title: "rebuilding without losing lots of environmental stuff"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by stardotstar on 2006-02-12
In my efforts to get my breezy system just right and while working on hand rolled kernels and lean builds I find that when blowing my system away even though I have backed up all my documents and some critical /etc files I cannot understand how to do a rebuild and fast restore of major preferences, profile stuff and environmental variables.  

What is the best way to do a complete clean install and then migrate a subset of prefered settings across to prevent a lot of work being repeated each time.


I know there must be a better way.  I have tried just copying some of my . files into my new home directory and this doesn't seem to work as well as I had hoped.

TIA

Will;

---

### Post by Turtle.net on 2006-02-12
When you do your installation, if you have a separate partition for /home, then do not format this partition on next install.
Like that you'll keep automaticaly your theme, icons, preferences...and personnal documents :)

---

### Post by stardotstar on 2006-02-12
[quote=Turtle.net]When you do your installation, if you have a separate partition for /home, then do not format this partition on next install.
Like that you'll keep automaticaly your theme, icons, preferences...and personnal documents :)[/quote]

got it - the key is a separate partition for /home (cool thanks) :mrgreen:

---

### Post by Turtle.net on 2006-02-13
Yep ;)
I think that maybe the best and easiest thing is to have these partitions : a /home for your files  a /opt for your installations from source and / for everything else
:)

---

### Post by poofyhairguy on 2006-02-14
Having a seperate partition for home is liek the best thing ever. I advise using the reiser file system for your / (root) partition. Its faster.

---

