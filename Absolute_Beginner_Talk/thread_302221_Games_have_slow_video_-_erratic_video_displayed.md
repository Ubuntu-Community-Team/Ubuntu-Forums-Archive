---
title: "Games have slow video - erratic video displayed"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2006-11-18
I have been running Ubuntu 6.10 for about a week and finally tried installing a few free games last night. The games appear to have some display problems that remind me of OPEN GL on a macintosh with OS X. Smooth is not a word I would use to describe the video on games. I have a fairly newer PC: HP Pavilion a1130n with an ATI Radeon Xpress 200 card - and I have tried EVERY update I could find for the card - including the fglrx thing. Does anyone know if I have to install an opengl driver or something? I sure like Ubuntu - but the video display is a bummer...

---

### Post by CatKiller on 2006-11-18
```
glxinfo | grep render
```

should tell you if you've properly installed your drivers. If it comes back with **direct rendering: Yes**, then it's something else.

---

### Post by nickpaton on 2006-11-18
I have an HP Compaq nx6125 laptop with a Radeon x300 graphics card, and even with rendering applied, it plays very few games - it just doesn't have the grunt.
Can you remember how much memory you assigned to the graphics?

Also could you tell me what happens when you run glxgears in a terminal.  Do the wheels turn smoothly?

I believe glxgears is installed by default but if typing glxgears returns nothing, try installing by

sudo apt-get install glxgears.

---

### Post by nickpaton on 2006-11-18
If you find that you don't have direct rendering, have a look at this post which explains how to install for radeon x series on Edgy:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

I use method 2.

Unfortunately you'll never get it very good, but a few games will run.

---

