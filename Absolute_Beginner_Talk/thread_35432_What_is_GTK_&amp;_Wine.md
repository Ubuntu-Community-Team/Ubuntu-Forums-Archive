---
title: "What is GTK &amp; Wine?"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by Mutant Human on 2005-05-18
Hi

there is so much discussion going on about wine and gtk.Can u please tell me what are they and how to use them?

thanks

---

### Post by Moobert on 2005-05-18
wine is:

'Wine is an Open Source implementation of the Windows API on top of X and Unix.'

[http://www.winehq.com/](http://www.winehq.com/)

Thus you can run alot of windows apps on unix with it... also Wine Is Not Emulator so the apps can run at good speeds, depending on how well the wine API supports them this can be alot faster or slower than windows. (but wines always being updated eg Direct 9 support is close to being added)

Also i while ago a company fromed wineX (now named cedega) to create a verson of wine to play the lastest windows games:

[http://transgaming.org/](http://transgaming.org/)

GTK is:

'GTK+ is a multi-platform toolkit for creating graphical user interfaces.'
and is currently used as a basis for most gnome apps

[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by az on 2005-05-19
In a Microsoft environment, everything is graphical.  If a program wants to create a window, it just tell the operating system to make on in the only way it knows how to.

In the open source environment, There is no graphical environment unless you install one.  Don't worry, the installer puts one there for you!  The point to remember is that apps do not all depend on the graphical environment to run..  This promotes stability.

Since open source is the product of many many people collaborating, there are usually many different ways of getting things done.  In the graphical desktop environment, for example, you can be running Gnome or KDE.  They both do the same thing.  They are completely different.

KDE uses the QT libraries to draw and utilise windows.  Gnome uses GTK libraries to do that.  KDE is a full-featured desktop.  So is gnome.  They have different programs for getting the same tasks done.

You get a choice.

I hope this makes things clearer.  Please ask further questions.  

Being that this is a great question, I hope you do not mind that I moved this thread to the Absolute Beginner's forum.  I think it will hep a lot of people there.

---

