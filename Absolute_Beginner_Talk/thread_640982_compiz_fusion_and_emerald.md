---
title: "compiz fusion and emerald?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2007-12-14
what exactly is the difference between these two things. are they  the same thing or different and can they be run togetther ?

---

### Post by SunnyRabbiera on 2007-12-14
emerald is really just a decoration so yes its possible to use emerald while running compiz

---

### Post by JillSwift on 2007-12-14
Compiz-fusion handles how things are finally drawn to the screen, blending alpha channeled graphics (and adding alphas to elements), as well as the 3D effects.

Emerald is a window decoration manager. It draws the boarders and window controls (minimize, close, etc). Its advantage over the usual window manager (Metacity, I do believe) is that it can make the window boarders with a final alpha channel, so that Compiz can take advantage of it and make for neat boarder effects.

I played with Emerald for a bit, and it makes for some really pleasant eye candy. But it slowed my screen draws down too much for me, so I returned to using Metacity.

---

### Post by allsys3 on 2007-12-15
Ive got both compiz fusion and emerald installed but when i go to advanced desktop effects setting and try getting the cube nothing happens. What am i missing

---

### Post by JillSwift on 2007-12-15
> **allsys3 said:**
> Ive got both compiz fusion and emerald installed but when i go to advanced desktop effects setting and try getting the cube nothing happens. What am i missingProbably nothing. Getting the cube is one thing, seeing it another.

First make sure you've 4 desktops. (well, 2 or more really, but 4 for a cube =^_^=)

Then, select the following plugins so you can play with he cube: (Some may already be "on")

Rotate Cube
Viewport Switcher

Those will let you move the cube around.

Nice additions:
Cube Reflection
Cube Caps

---

### Post by dpar on 2007-12-15
Also make sure you have compizconfig-settings-manager installed.

---

### Post by JillSwift on 2007-12-15
> **dpar said:**
> Also make sure you have compizconfig-settings-manager installed.oops, forgot to mention that =o.0=
It's only ***the point***, so i guess i forgot. =^_^=

---

### Post by jmckean on 2007-12-19
What is the default window decorator on ubuntu when using compiz-fusion?  I ask because something seems to have broken mine today and I am not sure what I am trying to fix.

---

### Post by NateMan on 2007-12-19
metacity is the default.
metacity --replace will run metacity
emerald --replace will run emerald

---

