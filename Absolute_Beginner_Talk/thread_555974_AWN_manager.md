---
title: "AWN manager"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-20
i finally got AWN manager set up to display the mac like dock 

but it is not working

when i go in to the awn manager i have 4 options 
General-- Is pretty much how it was on default

Applets- I am using LAUNCHER/TASKMANAGER--the main awn launcher applet

Launcher-- do i need one?

Theme-- I am using the glass beach alternitive version 1.1 auther was asher

the problem there is no dock on the bottom

---

### Post by Happy_Man on 2007-09-20
Do you have Compiz or Beryl running?

---

### Post by shortybookit on 2007-09-20
i have compiz

---

### Post by Happy_Man on 2007-09-20
Perhaps you have set it to autohide? It is in the AWN manager, general prefs, bar behaviour. 

If that doesn't work, open a terminal and enter ```
killall avant-window-navigator
avant-window-navigator
``` and see what ouput it gives.

---

### Post by shortybookit on 2007-09-20
the output was a mess 

including a working dock station that shows the active programs open 

is there a way i can add icons to the doc with out them being open applications?

another question i tried to make a transparent terminal window and i want it gone

the way it is set up right now is that there is no menu bar i.e. file,tools,view,edit

how do i get that bar back?

---

### Post by shortybookit on 2007-09-20
scratch that it does not work

it shows up when i did the terminal command 
but as soon as i close the terminal the dock also closes

---

### Post by shortybookit on 2007-09-20
anyone

---

### Post by shortybookit on 2007-09-20
could use a hint:)

---

### Post by crazee64 on 2007-09-20
> **shortybookit said:**
> scratch that it does not work

it shows up when i did the terminal command 
but as soon as i close the terminal the dock also closes

yes - this will happen. When you kill the terminal process you also kill it's children (including awn).
The output is the interesting part, that's why you run it in a terminal. Can you post the output?

---

