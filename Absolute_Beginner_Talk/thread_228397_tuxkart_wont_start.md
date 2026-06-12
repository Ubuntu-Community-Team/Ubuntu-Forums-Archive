---
title: "tuxkart wont start"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-08-03
This is what I get when trying to execute tuxkart..

Data files will be fetched from: '/usr/share/games/tuxkart'
PW: This is an *INDIRECT* rendering context.PW: That may be bad for performance.Data files will be fetched from: '.'


   TUXEDO T. PENGUIN stars in TUXKART!
               by Steve and Oliver Baker
                 <sjbaker1@airmail.net>
                  [http://tuxkart.sourceforge.net](http://tuxkart.sourceforge.net)


Kart 0 == 'tuxkart.ac'
Kart 1 == 'geekokart.ac'
Kart 2 == 'bsodkart.ac'
Kart 3 == 'gownkart.ac'
READY TO RACE!!
tuxkart: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
Aborted

//////////////

Any ideas on how to fix this?

Erick

EDIT::: I ran a few tests

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

glxgears -printfps
1686 frames in 5.1 seconds = 330.319 FPS
1680 frames in 5.2 seconds = 320.073 FPS

//////////////

Does this mean I will not get it working? :(

---

### Post by vruum on 2006-08-03
it just means that you'll need to get direct rendering working, there are a couple of different ways to do that, depending on which graphics card you have, and if you want to use open source or closed drivers. you could look through the hardware/video & sound forum, or post your info here.

---

