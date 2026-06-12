---
title: "[SOLVED] fluxbox menu help required..."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Adbru on 2008-01-12
Hi Guys,

Looking for some help :confused:

I was following Nathans menu guide ( [http://ubuntuforums.org/showthread.php?t=648036](http://ubuntuforums.org/showthread.php?t=648036) ) and have got myself in a hole !! 

I have tried to get back to the default setup but now only have a the "Fluxbox default menu" when i right click.

it only shows xterm,restart,exit.

as far as i can tell i have put everything back the way it was but obviously not :(

what code snipets do you need to see tell know what i've done wrong ???

thanks in advance

Adbru
(it was all going swimingly as well !!)

---

### Post by ajmorris on 2008-01-12
hi there,
can you please post your ~/.fluxbox/menu file?

---

### Post by yabbadabbadont on 2008-01-12
In case you haven't already, try working through RedSquirrel's Fluxbox menu customization guide.  (Nathan refers to it in his guide)

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

---

### Post by Adbru on 2008-01-12
Hi Guys,

Sorry for the delay, domestic life caught up with me :(

I followed part of RedSquirrels thread so my #/.fluxbox/menu file only contains:-
[begin]
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

my menu.bak file reads:-
[begin] (Fluxbuntu)
[exec] (Run...) {fbrun -title "Run..." -h 35}
[separator]
[exec] (Editor) {leafpad}
[exec] (File Browser) {rox-filer}
[exec] (Web Browser) {x-www-browser}
[exec] (Terminal) {uxterm}
[separator]
[include] (~/.fluxbox/menu)
[end]

I am running fluxbuntu 7.10 and my menu.bak may not have been the original :redface:

Thanks again

---

### Post by Adbru on 2008-01-12
hi guys,

i got it sorted :guitar:

thanks for your help 

till the next time :lolflag:

Adbru

---

