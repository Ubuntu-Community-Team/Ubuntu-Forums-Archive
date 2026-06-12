---
title: "how do i adjust double-click speed without gui?"
date: 2011-11-07
forum: Any Other OS
---

### Post by daniel227 on 2011-11-07
hello everybody,

how do i adjust double-click speed without gui?

i know the answer must be somewhere here already but all threads i looked into refer to the little gui that can be found on gnome desktops under appearance somewhere.
i don't have this, i'm using linux mint fluxbox (not much response on the forum there) which, i think, uses elements of both xfce and lxde, and fluxbox of course.
there's a setting in fluxbox but it affects only menus and window frames.

some config file i can edit?

thx.

daniel

btw, i'd like to have it slower. cramps my hand right now.

---

### Post by stinkeye on 2011-11-07
In unity I can get the current value with
```
gconftool-2 --get /desktop/gnome/peripherals/mouse/double_click
```

...and change the value with
```
gconftool-2 --type int --set /desktop/gnome/peripherals/mouse/double_click [COLOR="Red"]xxx[/COLOR]
```Where [COLOR="red"]xxx[/COLOR] is a number between 100 and 1000.

The actual settings file is at 
```
~/.gconf/desktop/gnome/peripherals/mouse/%gconf.xml
```

> btw, i'd like to have it slower. cramps my hand right now.
No single click setting for fluxbox?

**If using 11.10 (uses dconf)see** [COLOR="Red"][**_[COLOR="DarkRed"]here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11464458&postcount=8")[/COLOR]

---

### Post by Perfect Storm on 2011-11-07
Moved to Other OS/Distro Talk.

---

### Post by daniel227 on 2011-11-07
thanx to stinkeye, that did the trick!
yes, i think it's possible to have long single click hereabouts, mayb i should try it.

greetings to the other side!

and hello admin, my question is not specific to a certain distro, and it's certainly not "distro-talk".
it's a technical semi-noob quest for help. 
i think it would be good if this forum would stay open for all ubuntu derivates, too. 
there's really not much happening at the linux mint forum, esp not in the fluxbox section.
if you had moved it before stinkeye answered, mayb i'd still be cramping my index finger.

more awareness please.
but then, you probably do a lot of unpaid dirty work here, and i appreciate that. 

so, thx to all,

d.

---

### Post by Perfect Storm on 2011-11-08
Hi,

These forums are for Canonical supported distros, but we have Other OS/Distro for questions regarding non-Canonical supported distros. That includes ubuntu derivates too.

You can also check: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

