---
title: "Mouse problem in Ubuntu"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Jayme on 2007-01-08
hi there - I'm a complete beginner with linux and I've installed version 6.10 on my old desktop (It's a P4 2.0 ghz) and my mouse is completely messed up.  It has an extreme amount of lag..  I know the mouse works and I don't see why Linux wouldn't run on my machine...  Any ideas how to fix this?

---

### Post by moshuptrail on 2007-01-08
how is the video behaving?  (i.e. maybe it's not a mouse problem, but video?)

i've install U. on several machines, laptops, desktops, and never had a mouse issue.

do you have an unusual mouse?

---

### Post by Fireware on 2007-01-08
My install of Xubuntu was like that...I restarted my machine and then it worked fine.

---

### Post by Jayme on 2007-01-08
It's just a run of the mill Logitec mouse.  I don't think it's a video problem.  I've also tried restarting several times...  doesn't seem to help

---

### Post by moshuptrail on 2007-01-08
Do you know how to look at and post a section from your xorg.conf file?

It's located at /etc/X11/xorg.conf

the interesting section would begin with:
Section "InputDevice"
        Identifier      "Configured Mouse"
... and then other stuff.

---

### Post by Jayme on 2007-01-08
Hrmm...  no I have no idea...  I've never used linux before and I haven't even had time to mess around with it really because the mouse is too difficult to use.

---

### Post by moshuptrail on 2007-01-08
Click on Applications > Accessories > Terminal

this will open a command line "terminal"  (a bit like run cmd in XP)

from the command line, type 
gksudo gedit /etc/X11/xorg.conf

This will ask for your password, and then open a simple text editor

I'm guessing you can figure out how to navigate in that file.  Take a look at all the sections and see how they work.  It shouldn't be too hard to cut a section and paste it here.

Have fun!

---

