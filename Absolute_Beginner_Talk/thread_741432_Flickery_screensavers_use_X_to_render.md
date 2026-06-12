---
title: "Flickery screensavers: use X to render?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by DingsBumps on 2008-03-31
Using ubuntu 7.10x64, screensavers flicker a lot. Videos used to flicker in VLC, but following advice from another thread I switched the rendering to X instead of OpenGL and that solved my problem. Is there a way to do that with screen savers? 

I did try using the xscreensaver app instead, but that didn't help. Any ideas?

---

### Post by forrestcupp on 2008-04-01
You must be using the fglrx drivers for an ATI video card and running Compiz.

The answer to your question is no.  The only way to fix it is to turn Compiz off.  On an ATI card running Compiz, you will get flickering with anything that is opengl.  So either turn Compiz off, or choose a screen saver that isn't 3D.

...Or get yourself an nvidia card.

---

### Post by DingsBumps on 2008-04-01
Thats too bad :(
I really like compiz -- and I like cool-looking screensavers too. Damn.
Thanks anyways

---

