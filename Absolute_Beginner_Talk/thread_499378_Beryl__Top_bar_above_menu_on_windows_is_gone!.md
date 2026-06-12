---
title: "Beryl:  Top bar above menu on windows is gone!"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-07-12
Greetings:

I just installed NVIDIA-GLX and then Beryl.  I selected the Sky theme.  Now whenever I run an app, say Gedit, the very top of the window where it says GEdit is gone.  I have File > Edit, etc...  But where it says the name of the application and then the minimize, maximize and close buttons... that bar is gone!

Any idea why this would be?  Any idea how I could fix it?

Thanks in advance for any help you could provide!

Chris Farrugia

---

### Post by techno-mole on 2007-07-12
try adding this line to the screen section of etc/X11/xorg.conf

Option "AddARGBGLXVisuals"
it sounds like the window decorations are not working, this line should sort it.

---

### Post by Waappu on 2007-07-12
Hi

See if this helps
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631)

---

### Post by chrisf79 on 2007-07-12
> **techno-mole said:**
> try adding this line to the screen section of etc/X11/xorg.conf

Option "AddARGBGLXVisuals"
it sounds like the window decorations are not worknig, this line should sort it.

That fixed my problem!  Thanks so much!

---

### Post by techno-mole on 2007-07-12
glad i could help :)
cheers

---

### Post by techno-mole on 2007-07-12
may i suggest you do what i did (and im still doing ) i started a blank text editor file, and ive been adding all the things that sort out problems (such as the beryl issue you had) so i can go back to them when i need them, its kind of like a personal guide to ubuntu (at least the things i use and such like)
cheers

---

