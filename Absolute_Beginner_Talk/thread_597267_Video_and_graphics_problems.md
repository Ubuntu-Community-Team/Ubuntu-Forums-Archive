---
title: "Video and graphics problems"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by BLo on 2007-10-30
I'm kinda new to Linux and Ive just recently installed Gutsy. everything is going well except I'm having some problems with graphics and watching videos. I'm trying to get the graphics set up running smoothly with compiz enabled.

Firstly I have a HP Compaq 6710b laptop, with a Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) display driver. Ive had a search but I'm guessing I'm looking in the wrong place.

Compiz at first didn't work, im guessing because I got a Blacklisted PCIID '8086:2a02' found when running compiz.  I started compiz with SKIP_CHECKS=yes compiz and it worked so i added it to the compiz conf file.

Watchin videos was a problem as well, Totem and VLC would just exit when trying to play a video. I was getting 'BadAlloc (insufficient resources for operation)'  In totem and a similar error in VLC. I guessed it was something to do with compiz, which it was and disabling compiz made videos work fine. I also got video to work in VLC by changing the output module to OpenGL video output, but it is buggy especially when moving the window with VLC flickering and dropping frames

Also playing any 3d application like 3d chess freezes my comp with compiz on, or its very buggy and jumpy

 Can anyone help or suggest the best setup for intel graphics card or how to get everything working with compiz?

---

