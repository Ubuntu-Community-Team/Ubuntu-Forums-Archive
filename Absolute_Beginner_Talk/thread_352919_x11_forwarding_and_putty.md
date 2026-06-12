---
title: "x11 forwarding and putty"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by g3k0 on 2007-02-03
**Hey I heard that x11 forwarding can work with putty.  I have been unable to do this.  Can anyone help? I am trying to get a linux program working from putty.  When I click *SSH->X11->Enable X11 forwarding* I try it and it gives me this error. (with localhost:0.0 in the box)**

[bwhit132@csunix ~]$ echo $DISPLAY
localhost:0.0
[bwhit132@csunix ~]$ kcalc &
[1] 29359
[bwhit132@csunix ~]$ skcalc: cannot connect to X server localhost:0.0
[1]+  Exit 1                  kcalc

**If I dont click that enable I get this error.**

[bwhit132@csunix ~]$ kcalc &
[1] 29502
[bwhit132@csunix ~]$ kcalc: cannot connect to X server

[B]I know this works because it works from my friends ubuntu machine.  BTW kcalc is there just for example purposes.

also when I have enable clicked and I dont export the DISPLAY variable I get this[/B]


[bwhit132@csunix ~]$ kcalc &
[1] 29556
[bwhit132@csunix ~]$ kcalc: Fatal IO error: client killed

---

### Post by kylape on 2007-02-04
(I'm assuming you're in Windows) Do you have an X server installed?  If not, you can install cygwin at cygwin.com.  While installing make sure you install the Xorg base package.  Once it's installed, you can fire up cygwin and type 'startx' to get your xserver going.  Then you'll be able to use x11 forwarding with putty.

---

### Post by joeilynn on 2007-02-04
Message deleted.

---

