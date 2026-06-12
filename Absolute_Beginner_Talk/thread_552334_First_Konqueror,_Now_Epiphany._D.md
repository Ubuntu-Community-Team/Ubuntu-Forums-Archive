---
title: "First Konqueror, Now Epiphany. D:"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by DM was on fire! on 2007-09-16
> ashleigh1992@ubuntu:~$ epiphany

(epiphany:7797): Gtk-WARNING **: Unable to locate theme engine in module_path: "rezlooks",

** (epiphany:7797): WARNING **: An error occured while calling remote method: No reply within specified time


There isn't anyway to load rezlooks in terminal, is there?

---

### Post by DM was on fire! on 2007-09-16
*pokes thread back up*
D:

---

### Post by jordanmthomas on 2007-09-16
Does epiphany still work fine?  Chances are it's just a small bug in the theme you're using.  Do you have the rezlooks engine installed?

---

### Post by nonewmsgs on 2007-09-16
WAIT A MINUTE
epiphony is not the browser
$epiphany-browser 
is the browser

---

### Post by nonewmsgs on 2007-09-16
er that doesnt work on this one either.

try this 
epiphany %U

---

### Post by DM was on fire! on 2007-09-16
> **nonewmsgs said:**
> WAIT A MINUTE
epiphony is not the browser
$epiphany-browser 
is the browser

> ashleigh1992@ubuntu:~$ epiphany-browser
bash: epiphany-browser: command not found


> ashleigh1992@ubuntu:~$ epiphany %U

(epiphany:15377): Gtk-WARNING **: Unable to locate theme engine in module_path: "rezlooks",

And as for if I have the Rezlooks engine installed, I looked in Synaptic and I didn't have Rezlooks in there. I have Clearlooks, but not Rezlooks.
Epiphany has worked just fine before, but my computer froze and now it doesn't load.

---

### Post by jordanmthomas on 2007-09-16
Well, if you're using a rezlooks theme without rezlooks installed it really shouldn't crash programs, but try installing the rezlooks engine:
[http://www.gnome-look.org/content/show.php?content=39179](http://www.gnome-look.org/content/show.php?content=39179)

---

### Post by DM was on fire! on 2007-09-16
I looked at what the theme was I'm using, and it's a Rezlooks theme. That would most likely explain it.

One theme change and maybe I can get Epiphany again.

EDIT - Solved the rezlooks problem (thank you, Murrina Purple! <3), but I'm still having a problem with this:

> ** (epiphany:21344): WARNING **: An error occured while calling remote method: No reply within specified time


---

