---
title: "Windows borders dissappeared"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Reshuken on 2007-08-21
Well, I don't know what happened, but suddenly my windows borders don't appear anymore. Every time I log in a window with an error pops up:

   Cannot start the preferences applications for your
   window manager.
   Window manager "unknown" has not registrated
   a configuration tool

I have installed Beryl, although it doesn't start by default, so I'm assuming the "unknown" window manager is related to Beryl. I didn't have this problem before, and of course, I don't have this problem if I start session in "safemode" for Gnome. 

Any idea what could be wrong? Thanks in advance!!!

---

### Post by bren on 2007-08-21
you need to find the command to start the standard windows manager which is called metacity....

ALT-F2 ----- > metacity --replace &

might work.....

no guarantee

bren

---

### Post by Reshuken on 2007-08-21
Nevermind, I was able to solve the problem. I just needed to select Metacity as the windows manager again and all came back normally.

---

### Post by Reshuken on 2007-08-21
Thanks bren! It looks like you posted before me for seconds. I tried that, but for some strange reason I couldn't gel ALT+F2 to work, but in any case I was able to solve the problem. Thanks anyway!

---

### Post by mevets on 2007-08-21
kind of sounds like you installed beryl, but not emerald. If you want to use beryl and have window decorations, fetch the packages for emerald or switch your window decorator with the beryl-icon

---

