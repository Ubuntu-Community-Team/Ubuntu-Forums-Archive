---
title: "Play movie on log in?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by toxicgonzo on 2007-02-06
Hi,

I made a neat 3d animation in blender and I thought it would be cool if it played upon logging in.  I was wondering if it was possible to get rid of the usual window that shows after logging in and having it replaced with my animation?

---

### Post by apjone on 2007-02-06
should be , although i do not know how,

---

### Post by ComplexNumber on 2007-02-06
> **toxicgonzo said:**
> Hi,

I made a neat 3d animation in blender and I thought it would be cool if it played upon logging in.  I was wondering if it was possible to get rid of the usual window that shows after logging in and having it replaced with my animation?
i suspect that the only way for that to be possible is to turn the animation into an animated gif. then go to /usr/share/gdm/themes, find the theme that you are using(or select a  diffferent one), change the name of the wallpaper(ie change it from background.svg/background.png  to animated.gif(or whatever name you're going to call it). then you will need to alter the xml file in the theme so that it points to animated.gif instead.

---

