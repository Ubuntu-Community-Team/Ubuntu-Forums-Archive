---
title: "bmp"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Worp8d on 2008-04-19
Hi all,

I'm not quite an absolute beginner but I'm close and I don't know where to post this so I thought I'd start here.  I'm trying to install Beep Media Player 0.9.7,1 on a Dell Lattitude 531 running Ubuntu 8.04 (Hardy Heron).  I try the configure step (" ./configure ") and get the error message:

checking for X... no
configure: error: Cannot find X11 headers/libraries


I cannot find a solution for this problem despite having searched everywhere.  I have installed libx11-dev and libx11-xcb-dev but to no avail?  Any ideas?  Which forum should this ideally be in?

Cheers.

---

### Post by Perfect Storm on 2008-04-19
Try with libx11-dev

Why not give Audacious (in the repo) a try instead of bmp?

---

### Post by ibutho on 2008-04-19
Install xorg-dev and hopefully that will resolve your problem.

---

