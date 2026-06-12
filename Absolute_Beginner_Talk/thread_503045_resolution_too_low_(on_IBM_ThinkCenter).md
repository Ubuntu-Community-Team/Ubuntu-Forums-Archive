---
title: "resolution too low (on IBM ThinkCenter)"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ujwal10101 on 2007-07-17
hi, 
can you guys help increase my resolution. the highest in the preferences thingy is 1024*768. i want to put it to 1280*960. how do i edit the xorf file to get this. is the an alternate gui way to do it? i use ibm think center. i think the graphics card is Intel Corporation 82915G/GV/910GL Integrated.

---

### Post by Synth3t1c on 2007-07-17
try this in terminal:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back

Now we have a backup of this file, lets try this:

sudo gedit /etc/X11/xorg.conf

go to where you see modes, and add 1280x960 to each of those.

now restart x (ctrl + alt + backspace)


WARNING.  WRITE THIS DOWN!!!
if your x messes up, push shift - f1 or the like to get to a prompt. login with your username and password then type this:

sudo nano /etc/X11/xorg.conf

this will open up a simple editor.  undo the changes you made, and choose write out (either ctrl + x or o) and then close it (x or o as well, i mix them up).  restart x again.

---

### Post by ujwal10101 on 2007-07-18
i tried it out. but it didn't work. what could be the problem?

---

