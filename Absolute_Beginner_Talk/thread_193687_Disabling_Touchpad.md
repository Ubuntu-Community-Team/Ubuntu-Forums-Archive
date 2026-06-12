---
title: "Disabling Touchpad?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by camRW on 2006-06-10
I'm trying to disable my touchpad for an Inspiron 700m, but I'm having little luck.  The wiki only shows how to use a shortcut to turn it on/off, but I want it permanently off.  I've looked into xorg.conf, but I don't know what to edit.  Any ideas?

---

### Post by adam.tropics on 2006-06-10
In xorg.conf will be a section related to touchpad, comment out with# at the start of every line in that section between and including the lines 'section...' to 'endsection'.
There will also be a line in Section "ServerLayout" which you should also comment out.

---

### Post by LMelior on 2006-08-05
I have a problem with my laptop, a 5 year old inspiron.  My touchpad mouse buttons are broken, and every once in a while, my computer will freeze for half a second and then my cursor just goes absolutely crazy.  Even crazier than most people describe:  it cycles either vertically or horizontally all the way across the screen, constantly clicking on whatever it may happen to land on.  Sure it might have been funny the first time when it opened and closed my calendar about 50 times and opened up about 15 Trash folders, but as you might imagine it got old pretty quickly.  So I used these instructions to disable my synaptics touchpad.

It didn't fix the problem.  I didn't find any other relevant forum topics (and I used the instructions on here), so I posted here.  Any ideas?

---

