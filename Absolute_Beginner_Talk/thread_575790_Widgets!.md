---
title: "Widgets!?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-14
hey all,

I was wondering if there were are program for ubuntu that did widgets (like similar to Yahoo Widgets, Mac Dashboard or Vista widgets)

thanks!!

---

### Post by llamakc on 2007-10-14
GDesklets.

---

### Post by Frak on 2007-10-14
Gdesklets, adesklets, and superkaramba
If you are running gutsy, click on these links to install them
[apt:adesklets]("apt:adesklets")
[apt:gdesklets]("apt:gdesklets")
[apt:superkaramba]("apt:superkaramba")

Or in feisty, run this in the terminal
```
sudo aptitude safe-update
sudo aptitude install adesklets gdesklets superkaramba
```

---

### Post by llamakc on 2007-10-14
Frak, those links were nifty.

---

### Post by Frak on 2007-10-14
> **llamakc said:**
> Frak, those links were nifty.
Has to be one of the best new programs for Ubuntu since. Makes support for new users a heck of alot easier.

---

### Post by JasonBourneLinux on 2007-10-14
thanks guys!!

---

### Post by biggiec on 2007-10-14
Ok I have those packages installed, but I'm not sure to make them appear when I use the "Widget Layer" option in gutsy.

---

### Post by jordanmthomas on 2007-10-15
In the Widget Layer Options, go to the Behaviour tab.  In it there's a box called Widget Windows that will allow you to enter a regular expression for windows to match.  

[http://forum.compiz-fusion.org/showthread.php?t=558](http://forum.compiz-fusion.org/showthread.php?t=558) has a little information.  You can use the command xprop to get a bunch of information on a particular window, like its class or role or name (which you'd use in ccsm)

An easier way would be to use [screenlets]("http://www.screenlets.org/index.php/Home").  These have the option to set them as "widget" type so you don't have to fiddle with the regular expressions.

Hope this gets you going in the right direction at least.

---

