---
title: "xwinwrap"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-04-17
I got xwinwrap installed but when i start it in the terminal it ends up running like a screen saver.  I can not see the desktop but when my mouse goes over an icon it flashes briefly.  When i rotate the cube in beryl i can see the cube but the screen saver is not on each side of the cube but it is across the whole computer screen.  Just wonder what I have done wrong.
Thanks,

is what i have been entering on the screen
xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID

---

### Post by jordanmthomas on 2007-04-17
Are you using AIGLX or XGL?
I'm pretty sure xwinwrap doesn't work right with AIGLX.  (It doesn't on my Intel i915 at least)
Anything done in OpenGL will not transform as it should, and just goes over anything else.

If you're using XGL then I don't know what's wrong.

---

### Post by endlessurf on 2007-04-17
here's a great nub question,  how can i tell which one i'm running?

---

### Post by jordanmthomas on 2007-04-17
There's a few ways.

First off, you'd probably know if you're using XGL because it requires more steps to set up.
To check for XGL, type this in a terminal:
```
ps -A | grep XGL
```
If a process named XGL is returned, you are running XGL.

To see if you're using AIGLX, you can do this:
```
cat /etc/X11/xorg.conf | grep AIGLX
```
If a line labeled 
```
Option "AIGLX" "true"
``` is returned, you're using AIGLX.

Hope this helps.

(I think if you start beryl from a terminal it will tell you also, come to think of it)

---

### Post by endlessurf on 2007-04-17
nothing happened
:~$ cat /etc/X11/xorg.conf | grep AIGLX
:~$ sudo cat /etc/X11/xorg.conf | grep AIGLX
Password:
:~$ ps -A | grep XGL
:~$ sudo ps -A | grep XGL
:~$

---

### Post by jordanmthomas on 2007-04-17
Well, XGL definitely isn't running, so you're definitely not using it.

I don't use Ubuntu, so maybe their X is a little different than mine and you don't have to manually specify to use AIGLX in xorg.conf.  My guess is you're using AIGLX...which still doesn't help you much as I don't know of a solution to make xwinwrap work right.  I'm guessing the same sort of thing happens to you if you have the screensaver options / preview open and drag it around, right?

I would like a solution as well, so if anyone knows, feel free to jump in.

**and I checked, just typing beryl in the terminal will tell you what you're running.  It is possible you're using an Nvidia card and don't need AIGLX or XGL also.**

---

### Post by endlessurf on 2007-04-17
i typed in beryl and it said AIGLX,  thanks

---

### Post by endlessurf on 2007-04-17
Hey thanks for the help.  I just set up a xgl session and xwinworks.  I was just wondering what type of computer resources would be needed so the effects of xwinwrap would not be noticeable.  Thanks again

---

### Post by jordanmthomas on 2007-04-17
I'm not sure on that one.  I'm no hardware expert.  Maybe you could ask that one over at the beryl forums at [http://forum.beryl-project.org](http://forum.beryl-project.org) or even on these forums.

Good luck!

---

### Post by CowzRule on 2007-07-30
> **endlessurf said:**
> I got xwinwrap installed but when i start it in the terminal it ends up running like a screen saver.  I can not see the desktop but when my mouse goes over an icon it flashes briefly.  When i rotate the cube in beryl i can see the cube but the screen saver is not on each side of the cube but it is across the whole computer screen.  Just wonder what I have done wrong.
Thanks,

is what i have been entering on the screen
xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID

In your command change the -a to -b
like this```
xwinwrap -ni -argb -fs -s -st -sp [color=red]-b[/color] -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID
```
-a = above windows
-b = below windows

---

