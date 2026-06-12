---
title: "ubuntu server"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by thorson83 on 2007-06-07
I installed ubuntu desktop (feisty fawn) on my PC.  I tried installing ubuntu server and it did not load up gnome gui and I was having a hard time navagating around in the program.  I am trying to set up a web server for my daughter-in-law.  I have worked with windows most of my life and finally decided to learn linux and am enjoying the gnome gui on the desktop and am hoping that I will be able to install server with the gui

---

### Post by scxtt on 2007-06-07
the whole "point" of the server disk is to avoid the "overhead" of a gui (dedicate those resources to what the server is actually supposed to be doing) ... you can install a gui overtop a server install, you just have to decide if you want Gnome, KDE, XFCE, twm, etc. - then install the metapackage for it ...

---

### Post by thorson83 on 2007-06-07
Ok let say I want to load up the gnome gui what is the meta-package that I need to install.  I assume I would use get-apt

---

### Post by scxtt on 2007-06-07
i think the conventional install is **ubuntu-desktop**, so you'd do **sudo aptitude install ubuntu-desktop** ... that'll probably pull in a lot, so you might want to start w/ gnome-core (**sudo aptitude install gnome-core**) ... not sure how "messy" it'll get  ...

---

### Post by Buggin on 2007-06-09
is it possible to install just gnome-core and xserver and have something you can log in to without all the extra software?

---

### Post by scxtt on 2007-06-10
i'd start w/ just gnome-core and it should pull in what's necessary for X - can't say for sure tho ... i did a simulation of **aptitude -s install twm** and it seemed to pull in X, maybe start w/ that and if it works go for gnome-core ...

---

### Post by zvacet on 2007-06-10
You have desktop installed and all you have to do is to go to the synaptic<edit>mark package by task and select wich server you want(LAMP maybe?).

---

