---
title: "Trouble with command on startup"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by nutbastard on 2008-01-29
So i removed compiz yesterday, and as usual, it broke the default window manager metacity. and i've been through the forums a bit, no one seems to need to do what im doing...

every time i boot up, after gnome loads i have to open the terminal and enter:

metacity --replace

in order to get title bars and window borders to show up.

I tried making a file called .runmeta that resides in my home folder. it contains:

#!/bin/bash
metacity --replace

in terminal i then made it executable (supposedly) by entering:
chmod +x .runmeta

I then went into System>Preferences>Sessions and I clicked add, 
for name i put run meta, and for command i put:
~/.runmeta

but it no worky. what am i doing wrong here???

---

### Post by nutbastard on 2008-01-29
to elaborate a bit, i made the mistake of running

sudo aptitude autoremove compiz*

BEFORE i ran

metacity --replace

which people have told me would have avoided this problem entirely, if only i had done the replace command FIRST!

---

### Post by FuturePilot on 2008-01-29
That's a bug of removing Compiz, it breaks Metacity. I think perhaps the best and easiest solution is to leave Compiz installed but just turn it off.

---

