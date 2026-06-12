---
title: "Using projector with Ubuntu"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by iopo on 2007-03-13
Hi!

few days ago I had a presentation at school and I wanted to show off with my new Ubuntu installation. 

After a few attempt to make the projector work, I rebooted the computer with the projector plugged and it finally worked. 

Anyway, for some reason I was able to see projected just some 80% of my screen,  making the presentation rather hard! Does anyone knows how to modify the size of the screen when using a projector?

Thanks!

---

### Post by Belyel on 2007-03-13
The only luck I've had with a projector is using either xinerama or twinview (ati vs nvidia, basically) and setting them to "clone" mode.  Alternately, as you found, if you restart your computer 'buntu will auto-detect the projector.  THe reason you were missing part of the screen probably lies in the resolution of the projector.  If the projector is set up for 1024x768 resolution and your laptop is running at 1280x1024, the output to the projector will also be 1280x1024, resulting in an output that will pan as you move your mouse around.  Different projectors handle this differently, some will scale it automatically, but the surefire way to have your whole presentation show up is to change your screen resolution to match the projector.  It will be ugly on your laptop, but your presentation will be beautiful :).

---

### Post by iopo on 2007-03-14
Thanks Belyel!

That's exactly what happened!

is there an easy way to switch screen resolution back and forth?

By the way, I noticed that projectors seems not very popular in the ubuntu community (i couldn't find many threads dealing with this topic). It's a pity: that's exactly one of the things non-IT guys use the computer for! And it's also a good way to attract attention of other people!

Thanks!

---

### Post by David Haas on 2007-03-19
To change your laptop's screen resolution click on System>Preferences>Screen Resolution, and in the Screen Resolution Preferences dialog box select from the menu of resolutions.
David

---

