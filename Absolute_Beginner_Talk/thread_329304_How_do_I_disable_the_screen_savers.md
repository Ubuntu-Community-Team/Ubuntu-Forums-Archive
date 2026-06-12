---
title: "How do I disable the screen savers"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by cap10kirk on 2007-01-01
I want to disable all screen savers and hibernation mode. When I'm away from my box for a period of time, the box seems to go into some type of hibernation mode. And I can not get the box out of this hibernation. I always have to hit my RESET button.

You help is much appreciated
Kirk, out.

---

### Post by bapoumba on 2007-01-01
Hello :)

> System > Prefs > Screen saver > untick Activate... and Lock ...
> System > Prefs > Power management > Put computer to sleep = never

---

### Post by cap10kirk on 2007-01-01
> **bapoumba said:**
> Hello :)

> System > Prefs > Screen saver > untick Activate... and Lock ...
> System > Prefs > Power management > Put computer to sleep = never

Thanks for the quick reply, bapoumba

Kirk

---

### Post by bapoumba on 2007-01-01
Welcome, Captain. Engage ;)

---

### Post by 92mr2 on 2007-01-08
Hi,

An very newbie.  Atually I'd like to get my screen savers TO work.  Ubuntu has some very cool ones but I can't seem to make it function.
I've been to preferences and clicked all the obvious buttons but what am I missing?

thanks

---

### Post by bapoumba on 2007-01-08
@ 92mr2 : in > System > Preferences > Screensaver, tick "Activate screen saver when computer is idle" and select when the computer is to be idle (I have a laptop, I choose 10 mins).
I do not like screensavers that much, I just selected a blank screen. Guess you can pick random or any other one you like from the list.

---

### Post by 92mr2 on 2007-01-08
thanks bapoumba,

Unfortunately I tried that first but no go.  It's pretty intuitive on how to do it but it just won't start the screen savers on 10 minutes, or 2 minutes or anytime, but thank you.

---

### Post by bapoumba on 2007-01-08
run **gconf-editor** from a terminal, > apps > gnome-screensaver
Could you link a screenshot ? Are you using dapper or edgy ? I just realized some commands do not run anymore for screensavers or even gconf-editor from the command line on edgy. I'm looking into it.

---

### Post by baldmosher on 2007-01-12
My problem is a bit more troublesome. Turns out that some of the default (OpenGL?) Dapper 3D screensavers cause my PC to hang or crash entirely. Others work fine. Some work fine then hang. Unfortunately it's set to one that crashes the system (I assume it's a dodgy video driver error as my CRT pops up the OSD and refuses to display "165Hz") so I can't change it to anything else.

Only solution at the moment is to move the mouse every 9 mins 30 secs to stop the s/s appearing :D 

Is there a command line to disable them?

EDIT: spoke too soon, just read the above post! Sorted it! Think I need to ask the video driver question elsewhere though

---

### Post by awperk on 2007-05-12
i don't use a screen saver but i have a question related to power management. i have ubuntu set to turn my lcd off after so long but i'd like to have it also set to go to sleep after a period of time too. my problem is that ubuntu only gives you the option of putting your computer to sleep after any time less than or equal to 1 hour. i like to copy dvd's and download torrents so i don't want my box to go to sleep that soon. is there any tweak or special applet that i could use to do this?

-thanks

---

### Post by bapoumba on 2007-05-13
> **awperk said:**
>  ubuntu only gives you the option of putting your computer to sleep after any time less than or equal to 1 hour. 
Hello,

which menu are you talking about? In xfce (not tried in gnome, but I can have a look), I can choose 4 digits periods of time. I this from the screensaver menu?
I do not use screensavers either, just blank screen.

---

### Post by awperk on 2007-05-13
i use gnome and it's under system>prefs>power management and then the ac power tab.

-thanks

---

