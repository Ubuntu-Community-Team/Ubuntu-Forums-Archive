---
title: "gl-117 freezes when move mouse"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by olejorgen on 2007-05-23
I'm running feisty and gl-117 from the repos (feisty)

When I start the game, I get a steady ~150 fps, but as soon as I move the mouse the game freezes (not the music)

I get no error output even when running with -d5

Anyone?

---

### Post by Pragmatist on 2007-05-25
gl-117 website indicates that GLUT or Mesa-GLUT are needed for mouse support.  Check in Synaptic and make sure you have "freeglut3" installed.  You might also want to install the debug and development packages:

freeglut3-dbg
freeglut3-dev

---

### Post by olejorgen on 2007-05-25
Sure, I've got freeglut installed. I installed gl-117 from the repos (with synaptic) so it shouldn't be any dependency problems (?)

---

### Post by Pragmatist on 2007-05-25
> **olejorgen said:**
> Sure, I've got freeglut installed. I installed gl-117 from the repos (with synaptic) so it shouldn't be any dependency problems (?)

Yes, but do you have the other two packages installed?
freeglut3-dbg
freeglut3-dev

It isn't necessarily a dependency issue.  The freeglut3-dbg, for example, might help you debug the problem.

Anyway, it is easy enough to find out.

---

### Post by forestcomber on 2008-06-15
Was a solution found for this issue ?  I have the same problem.  Running ATI AIW 9600XT video adapter.  All other 3D apps and games seem to run fine, except GL-117.

---

