---
title: "Ubuntu 6.06.1 on MacBook - right mouse button"
date: 2006-09-21
forum: Apple PPC Users
---

### Post by anzevi on 2006-09-21
Hi!

I have a success story about running Ubuntu 6.06.1 on MacBook. The things are working "out of the box" the only thing that i really can't get to work is right mouse button click, and i need it bad! :mad: 

I've google for it, tryed a bunch of different things from different manuals but nothing seams to work.

Can someone please direct me into the right way on how to map touchpad/keyb keys --> right mouse button click, PLEASE :KS 

I also sow on Gentoo on MacBoook project site that scrooling with 2 fingers and stuff like that works? Anyone got this working on Ubuntu?

Thank you

---

### Post by anzevi on 2006-09-22
Note to myself (and the others):

Got it working by cereating .xmodmap file in my home folder.
It looks like this:

#!/bin/sh
xmodmap -e "keycode 108 = Pointer_Button3"
xkbset m

Save it and put it into the "startup programs" menu in System --> Prefrences --> Sessions

Logout. The right "small enter" button is now emulated for a right click.

---

### Post by markd1216 on 2006-09-26
Credit goes to various posters as I was scanning through this forum -- F12 seems to be a simple solution.

Mark

---

### Post by Nikusan on 2006-10-17
What about iSight?

---

