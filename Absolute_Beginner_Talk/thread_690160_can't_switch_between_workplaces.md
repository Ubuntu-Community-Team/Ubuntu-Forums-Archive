---
title: "can't switch between workplaces"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Pulka on 2008-02-07
hi!


ok, have been working with gutsy for some time now, but this is weird. I can't switch between workplaces. I'm using compiz, i have 4 desktops, but when i click on them, nothing happens.
Any ideas?

---

### Post by ferdostar on 2008-02-07
> **Pulka said:**
> hi!


ok, have been working with gutsy for some time now, but this is weird. I can't switch between workplaces. I'm using compiz, i have 4 desktops, but when i click on them, nothing happens.
Any ideas?

Did you try to turn off effects?

---

### Post by Pulka on 2008-02-07
yes...it works without effects. The point is, it shouldn't be a problem. Have no problems in other computers

---

### Post by ferdostar on 2008-02-07
> **Pulka said:**
> yes...it works without effects. The point is, it shouldn't be a problem. Have no problems in other computers

Maybe you can try to reinstall compiz or try to manage your video card driver :confused:

---

### Post by osos on 2008-02-07
compiz uses single desktop for it's effects etc.
it also overrides what ever key combos you have for switching. 
if my memory serves me right you can switch desktops with your mouse wheel by default.
why not use the methods compiz has to offer for multiple "desktops"?

---

### Post by ferdostar on 2008-02-07
> **osos said:**
> compiz uses single desktop for it's effects etc.
it also overrides what ever key combos you have for switching. 
if my memory serves me right you can switch desktops with your mouse wheel by default.
why not use the methods compiz has to offer for multiple "desktops"?

try removing Beryl-manager...

and try it...and also check if all the plugins u said are enabled and correctly configured....

---

### Post by jaytek13 on 2008-02-07
Does cntl-alt-left/right arrow work?

---

### Post by Pulka on 2008-02-07
> **jaytek13 said:**
> Does cntl-alt-left/right arrow work?

no. 

i have activated the compiz options:  expo, scale, snapping windows and place windows

---

### Post by Pulka on 2008-02-08
solved.

all it takes is to activate some compiz options: desktop wall and viewport switcher

---

### Post by atomkind on 2008-05-25
Wow! I feel pretty dumb right now... I had enabled 'desktop cube' but forgot to enable 'rotate cube' even though I've set up compiz before on other machines... (Then again, rotate cube should be enabled by default when you enable desktop cube... why would anyone want a cube if you're not able to rotate it or switch between workplaces?)

---

### Post by lyran on 2008-07-12
Not checking "Rotate Cube" stumped me too for a bit. 

Selecting "Desktop Cube" should automatically enable "Rotate Cube."

---

### Post by steve8track on 2008-07-12
In case anyone needs it, here are other reasons I've found that the cube won't rotate:

Turn on appropriate plugins, either the wall or the cube, and the rotate cube plugin, as suggested above.

Compiz uses one desktop stretched out, so make sure that in the General Options => Desktop Size you set the Number of Desktop ironically to 1, while horizontal size should be greater than on (4 by default), and for the cube vertical size shouldn't be greater than 1.  If you set the vertical size to 2, for example, the cube won't rotate up or down to the other level, and you will have to use the desktop wall or expo to get to the other rows.

Also, compiz seems to get confused if you rotate the cube quickly with the mouse.  It doesn't seem to know what desktop it is on anymore.  To fix it, I use the Expo plugin to help compiz know what desktop it is on again by selecting one.  You may also be able to use some window switching plugin, like pressing alt+tab, or reloading the window manager.

I hope this helps someone.

Steve

---

