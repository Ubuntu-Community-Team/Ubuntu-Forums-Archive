---
title: "Fluxbox!!"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2007-12-10
I installed Fluxbox in Gutsy so that I could run this old system better, and when I get in, all there is is a bar. I click the bar, and a menu pops up with settings for it. I then right click on desktop, nothing is happening. I middle click, and that is only workspace options.

WHAT DO I DO!?!? I have no idea even how to shut the machine off correctly, and I cannot even get into a terminal except with pressing CTRL+ALT+F4!!

HELP please!!

---

### Post by fedex1993 on 2007-12-10
umm do you still have gnome installed? if you do boot into gnome and then go into the terminal and type sudo update-menus or its sudo update-menu and then boot back up into fluxbox and then richclick or center click and then it should come up with a menu

or you can just go into the terminal and type those commands

---

### Post by skymera on 2007-12-10
right click brings up the menu.

try

sudo apt-get upgrade

i personally dont like fluxbox, its very very very dull.

---

### Post by Tristicus on 2007-12-10
Lawl, I forgot to follow the other guys instructions, and update the menus...hopefully this helps....sorry for being a total noob.

---

### Post by Pumalite on 2007-12-10
[http://fluxbox.sourceforge.net/docs/en/faq.php](http://fluxbox.sourceforge.net/docs/en/faq.php)

---

### Post by Pumalite on 2007-12-10
[http://forums.debian.net/viewtopic.php?t=5382](http://forums.debian.net/viewtopic.php?t=5382)

---

### Post by yabbadabbadont on 2007-12-10
The fluxbox package, as distributed with Gutsy, has a broken menu.  There are a few threads about it around here somewhere.  RedSquirrel has an excellent tutorial on correcting this as well as customizing your menu.

[http://www.ubuntuforums.org/showthread.php?t=371144](http://www.ubuntuforums.org/showthread.php?t=371144)

---

### Post by Tristicus on 2007-12-10
Man, I do not like Flux. What is the code to un-install it?

---

### Post by SOULRiDER on 2007-12-10
try
```
sudo aptitude purge fluxbox
```

---

### Post by corney91 on 2007-12-10
> **Tristicus said:**
> Man, I do not like Flux. What is the code to un-install it?

```
sudo apt-get remove --purge fluxbox
```

The --purge removes the config so if you're going to reinstall it leave that out

---

### Post by Tristicus on 2007-12-10
Thanks!

---

### Post by bodhi.zazen on 2007-12-10
> **yabbadabbadont said:**
> The fluxbox package, as distributed with Gutsy, has a broken menu.  There are a few threads about it around here somewhere.  RedSquirrel has an excellent tutorial on correcting this as well as customizing your menu.

[http://www.ubuntuforums.org/showthread.php?t=371144](http://www.ubuntuforums.org/showthread.php?t=371144)

yes, IMO it is too bad the default install of fluxbox in so ...  dull ?

To get a feel of what fluxbox can do, take a look at something like Fluxbuntu, Wolvix, or March Linux.

For a very nice (IMO) menu , see : [http://code.google.com/p/marchfluxmenu/](http://code.google.com/p/marchfluxmenu/)

Although I admit I customized that menu.

---

### Post by Tristicus on 2007-12-10
When some people talk about Flux, it has always interested me, because it looked so customizable and nice when worked out, but I am still and noob, and prefer full GUI, such as Ubuntu. That is why I do not like it.

---

### Post by bodhi.zazen on 2007-12-10
> **Tristicus said:**
> When some people talk about Flux, it has always interested me, because it looked so customizable and nice when worked out, but I am still and noob, and prefer full GUI, such as Ubuntu. That is why I do not like it.

I understand. I had the same experience the first time I installed Fluxbox.

I use it now because it is unobtrusive and, well, I have more experience. But you have hit the nail on the head. Some experienced users want a light yet customizable window manager without all the bells and whistles.

---

### Post by Tristicus on 2007-12-10
Yep, and I am un-experienced and want a very light system, and thats not gonna happen for now lawl. I will probably mess around with it again after I get my new system up and running.

Both machines dedicated to Linux:
Current: P3 500mhz, 256mb RAM, 20gb HDD, crap video card
Future (got everything except wireless card, video card, case, PSU): P4 Celeron (Forgot ghz), 1.5gb RAM, 40gb HDD, average video card probably.

---

### Post by bodhi.zazen on 2007-12-10
I would give XFCE (xubuntu) a try.

---

### Post by Tristicus on 2007-12-10
I did. It was okay, but I found I didn't like it either....I can't afford to be this picky lawl.

---

