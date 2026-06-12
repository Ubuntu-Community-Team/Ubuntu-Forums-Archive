---
title: "ive lost the add/remove option......"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-08
Hello.
i seem to have lost the add/remove option that is normally the last option under applications, it was there and now it isnt ? is there anyway i can get it back ? i dont know when it went, but ive just gone to install some things and its gone ?
cheers.

---

### Post by dannyboy79 on 2007-02-08
you can always use synaptic to install stuff, it's under system, admin. otherwise you could try to  reconfigure your (pardon my french) start menu. you would just go to accessories and hit alacarte menu editor and then you should be able to put a check mark next to add-remove programs hopefully. otherwise you can always use the the terminal. sudo aptitude search "program". if it finds it, then do sudo aptitude install "program". good luck.

---

### Post by techno-mole on 2007-02-08
i dont seem to have an alacarte menu editor ? 
i take it that anything that you can install from the install disc can be found under synaptic ?
cheers

---

### Post by dannyboy79 on 2007-02-08
i believe so. you have to have alacarte, it comes by default. just look in another location or type in at the command line, gksudo alacarte. if that's not the command, than do a locate alacarte to find out what exactly the command is.

---

### Post by xpod on 2007-02-08
If your using edgy it`s just called "menu layout" now and it`s in "System>administration" or you can just right click your menus and "edit menu".

EDIT:System/preferences even:-)

---

### Post by roel46 on 2007-02-08
If you lost your alacarte menu editor (i.e. system > preferences > menu layout) and also your "Add/Remove..." (i.e. applications > add/remove...) then your menu seems to be damaged. You could repair it by calling alacarte from the command line (= shell, terminal): alacarte.

Yes, you can install with "synaptic package manager". It is an advanced "add/remove...".
Ciao, Roel.

---

### Post by tc811 on 2007-02-08
Hi,

I'm experiencing the same problem as the OP, except I can access the menu layout option.  But I can't find add/remove programs anywhere.

Thanks for the help.

-tc

---

### Post by techno-mole on 2007-02-08
appologies for the mix up, i have the menu editor - system/preferences/menu layout, but there is no icon for the add/remove option ? does it matter that its not there, apart from the fact that i have to go through synaptic or automatix, but to be honest i only used the add/remove to install stuff of the disc.
cheers for the help.

---

### Post by tc811 on 2007-02-08
bump; does anyone know how to resolve this issue?

---

### Post by Dr Small on 2007-02-08
I had a similar problem here:
[http://ubuntuforums.org/showthread.php?t=354644&highlight=add+remove](http://ubuntuforums.org/showthread.php?t=354644&highlight=add+remove)

I had lost my Add/Remove Panel, so here's the command to reinstall it:
```
sudo apt-get upgrade gnome-app-install
```


Dr Small

---

### Post by tc811 on 2007-02-09
thanks for the help.

for some reason it got 'uninstalled', and i had to go into the synaptic manager to install it back, so everything is working good now.

---

