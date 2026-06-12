---
title: "if i get rid of gnome..."
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-11-22
i'm worried i'll have trouble getting back to a graphical thingy. i once installed KDE and uninstalled gnome. i don't remember what the error message was, but i was in some kind of console mode and couldn't get out, nor understand the instructions i was being given. a couple of other times, i have rebooted and ended up with just a console. i end up rebooting and hoping i end up in the login screen. so, if i want to get rid of gnome and i end up in console mode, how would i get a login screen (i'd be using fluxbox)? is it a good idea to dump gnome once i decide i like fluxbox?

---

### Post by 23meg on 2005-11-22
Not a good idea if you're not very low on HD space, since you lose GDM, thus the ability to select what WM to use with a GUI.

---

### Post by aysiu on 2005-11-22
[QUOTE=23meg]Not a good idea if you're not very low on HD space, since you lose GDM, thus the ability to select what WM to use with a GUI.[/QUOTE] But if you install KDE, don't you replace GDM with KDM?

---

### Post by 23meg on 2005-11-22
[QUOTE=aysiu]But if you install KDE, don't you replace GDM with KDM?[/QUOTE]
The OP says they'd like to install fluxbox, not KDE.

---

### Post by aysiu on 2005-11-22
[QUOTE=23meg]The OP says they'd like to install fluxbox, not KDE.[/QUOTE] I was referring to this part of the original post: > i once installed KDE and uninstalled gnome. i don't remember what the error message was, but i was in some kind of console mode and couldn't get out, nor understand the instructions i was being given.

---

### Post by 23meg on 2005-11-22
[QUOTE=aysiu]I was referring to this part of the original post:[/QUOTE]
Ok, but the current intent of the OP is to install Fluxbox and get rid of Gnome, not install KDE; hence my answer. 

I haven't done this myself but in a scenario where neither GDM nor KDM are available, the way to launch X with fluxbox would be to modify the ~/.xinitrc file and put the following into it```
 exec startfluxbox
``` and start X manually with ```
startx
```.

---

### Post by marksi on 2005-11-22
i've moved from gnome to xubuntu (xfce) and login from the command line with *startx*. it works well and it's also faster. you can always install gdm or kdm later if you want a graphical interface

---

### Post by 23meg on 2005-11-22
But GDM/KDM would have lots of Gnome/KDE library dependencies, which would defeat the point here. Is there such a thing as a non-DE dependent graphical display manager / session chooser? Maybe XDM?

Anyway, for a better reference on how to create customized X sessions, take a look at Stormy's guide [here]("http://ubuntuforums.org/showthread.php?t=79263").

---

### Post by az on 2005-11-22
Except for themes, KDM and GDM are DE agnostic.  You can chose whatever session you like.  You will consume more memory if you boot into KDM and then use Gnems or vice versa (GDM - KDE) but it should never result in you not being able to get into X (The graphical interface)

Usually, if a package installation fails, you just have to reinstall it and it fixes everything.

sudo apt-get -f install

But installing icewm, kde or anything of the like should not cause you any problems.  You can pick your session at the GDM login screen (or KDM)

---

### Post by fuscia on 2005-11-22
i only have a 10GB HD, but i don't think i've had less than 6GB of free space for two years. e-mail, playing with pics (avs, photo editing, nothing huge) and being an internet nuisance are all i really do with my computer. i have gnome set up nicely, so i should probably leave it, since i change my mind every five seconds. would leaving gnome on my computer have any derimental effect on the speed of fluxbox?

when i get a laptop (doesn't look like santa is planning on it), i'm going to have another shot at a server install. at this very moment, i envision putting fluxbox on it. so, i could put fluxbox on it without gdm or kdm and still login to flubox's gui and just have no graphics for a login?

thanks for all the responses.

---

### Post by Brunellus on 2005-11-22
having gnome on your computer has no effect on fluxbox performance.  I do this, and I know.

There are howtos out there for installing a minimal system with fluxbox using xdm as the display manager.  I'm presently working on one for the wiki;  should be done by the end of the Thanksgiving holiday.

---

### Post by 23meg on 2005-11-22
[QUOTE=fuscia]would leaving gnome on my computer have any derimental effect on the speed of fluxbox?[/QUOTE]
Other than disk space, no.
[QUOTE=fuscia]
when i get a laptop (doesn't look like santa is planning on it), i'm going to have another shot at a server install. at this very moment, i envision putting fluxbox on it. so, i could put fluxbox on it without gdm or kdm and still login to flubox's gui and just have no graphics for a login?
[/QUOTE]Must be possible the way I described in post #6.

---

### Post by N8K99 on 2005-12-06
[QUOTE=23meg]But GDM/KDM would have lots of Gnome/KDE library dependencies, which would defeat the point here. Is there such a thing as a non-DE dependent graphical display manager / session chooser? Maybe XDM?

Anyway, for a better reference on how to create customized X sessions, take a look at Stormy's guide [here]("http://ubuntuforums.org/showthread.php?t=79263").[/QUOTE]
If you use Enlightenment DR17 there is a graphical login called Entrance. I have had it working from the repositories, however as I now have a fresh install with e17 from CVS; which puts everything in /opt/ i am unsure of how to config my .xinitrc to get entrance to be the login screen on boot.

---

### Post by MasterOfDisaster on 2007-04-09
Not sure if this will work in the slightest, but can you change /etc/X11/default-display-manager to 'entranced'?

---

### Post by adam.tropics on 2007-04-09
Awesome, so now we have the 'unanswered posts team', the 'beginners team', and a new COLD CASES team!  10/10 for answering though!

---

