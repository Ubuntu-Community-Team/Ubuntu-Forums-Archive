---
title: "Americas army issue?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-09-08
not sure whether to post here or not.

its not really an ubuntu problem, its AA

i heard tyat changing rendering from OpenGL to Software can sometimes help weith intergrated cards.

so i did, it closed down and dosent even start up!

is there a way to change it back to OpenGL?

---

### Post by skymera on 2007-09-08
any ideas?

---

### Post by overdrank on 2007-09-08
> **skymera said:**
> any ideas?

Hi did you reconfigure your xorg?

---

### Post by skymera on 2007-09-08
no :)

i went into settings in the GAME.
selected software instead of openGL and now its pooped up.

i need to change it in game :) but dunno how, it no load!

---

### Post by overdrank on 2007-09-08
> **skymera said:**
> no :)

i went into settings in the GAME.
selected software instead of openGL and now its pooped up.

i need to change it in game :) but dunno how, it no load!

My apologies I totally miss understood the question. :???:

---

### Post by skymera on 2007-09-08
i didnt explain very well :P

ive uninstalled and going to reinstall, but im not sure that will fizx it.

when i uninstall are my personal settings, like grpaihcs and rendering etc stored?

for the moment, SOLVED :D

AA forum has given a solution:

>  Open ArmyOps.ini
Locate: [Engine.Engine]
Remove the ; before ;RenderDevice=OpenGLDrv.OpenGLRenderDevice
Add ; before the render device currently being used.


---

### Post by skymera on 2007-09-08
there is no armyops.ini??????

what can i do?

---

