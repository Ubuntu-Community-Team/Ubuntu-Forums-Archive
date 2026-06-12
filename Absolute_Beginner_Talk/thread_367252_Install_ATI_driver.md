---
title: "Install ATI driver"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by grogger13 on 2007-02-21
Im trying to get my ATI driver setup for Beryl and i was given this command
mike@mike-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


but i was supposed to get something like
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)

I have an X1400 so im not sure is the 9700 would be the same but i know its not Mesa.

---

### Post by Maestro23 on 2007-02-21
If you are having trouble with the HOW-TO and command line, just use the Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by grogger13 on 2007-02-21
do i have to disable any of the things i configured already

---

### Post by grogger13 on 2007-02-21
One problem with Envy script.

It tells me to close X windows by press CTRL+ATL+F1, but it changes my screen into a bunch of scattered ubntu red and orange and black lines horizontally and in boxy disorgized fashion.

I dont see any terminal.

---

### Post by unknownsoldierX on 2007-02-23
> **grogger13 said:**
> One problem with Envy script.

It tells me to close X windows by press CTRL+ATL+F1, but it changes my screen into a bunch of scattered ubntu red and orange and black lines horizontally and in boxy disorgized fashion.

I dont see any terminal.

I have the same problem.  I hit CTRL+ALT+F1 and I get a black screen with a big, multi-colored rectangle.  I have to three-finger salute to reboot.

Somebody help us, please!

---

### Post by nickoli_02 on 2007-02-23
I had the same problem when I was trying to get beryl to work. It's not beryl's fault, obviously, it's because you have to disable composite in xorg.conf. This, unfortunately, doesn't play nice with fglrx I guess. I never did get it figured out, I ended up going back to Dapper. Dapper is nicer for me anyway, I'll probably stick with it until I have to upgrade again.

---

