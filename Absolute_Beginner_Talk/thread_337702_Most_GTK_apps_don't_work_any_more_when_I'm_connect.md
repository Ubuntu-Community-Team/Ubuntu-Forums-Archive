---
title: "Most GTK apps don't work any more when I'm connected to the internet!"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2007-01-13
Has anyone ever heard of anything like this before?  I setup my wireless card - Broadcom 4306 - using ndiswrapper, and I can get 56 kbps, which is great, until I try, for instance, sudo gedit in the terminal.  Gedit just doesn't pop up.  sudo nautilus does the same thing.  To make matters worse, the panels and the desktop will occasionally decide not to work.  But as soon as I disconnect from the network, everything works fine again.  I thought maybe the network manager applet was the problem, but I tried connecting with the built-in ifup and that didn't work either.  Can anyone help me out with this?

---

### Post by ComplexNumber on 2007-01-13
> sudo nautilusalthough i don't have a solution to your problem (and i've never heard it mentioned before), its worth pointing out that you should ideally be using gksudo instead of sudo when running graphical applications. just use sudo for running scripts and non-graphical commands such as rm, chmod, etc.


> To make matters worse, the panels and the desktop will occasionally **decide not to work**.what exactly do you mean by this? ie decide not to work in what way?

---

### Post by crazybrit4967 on 2007-01-13
> **ComplexNumber said:**
> although i don't have a solution to your problem (and i've never heard it mentioned before), its worth pointing out that you should ideally be using gksudo instead of sudo when running graphical applications. just use sudo for running scripts and non-graphical commands such as rm, chmod, etc.


what exactly do you mean by this? ie decide not to work in what way?They just freeze and clicking on them does nothing.  Sometimes all the desktop icons disappear.

---

