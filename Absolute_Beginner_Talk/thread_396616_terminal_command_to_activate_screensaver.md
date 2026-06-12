---
title: "terminal command to activate screensaver"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-03-29
hello,
I would like to activate screen saver by using terminal command. Does anybody know what is the terminal command for that?
I will use this when I leave my desk for short breaks.

Thanks....

---

### Post by Delvien on 2007-03-29
> **mozkaynak said:**
> hello,
I would like to activate screen saver by using terminal command. Does anybody know what is the terminal command for that?
I will use this when I leave my desk for short breaks.

Thanks....


Left CNTRL + Left ALT + 'L'  

Will lock your screen and should start your screensaver shortly after.

---

### Post by Sturmeh on 2007-10-14
If i wanted a script to initiate the screensaver, what command would I use?

---

### Post by Farhan on 2007-10-14
> **Sturmeh said:**
> If i wanted a script to initiate the screensaver, what command would I use?
try these:
gnome-screensaver --help
gnome-screensaver-command --help

---

### Post by Sturmeh on 2007-10-14
Many thanks...

The correct command is. "gnome-screensaver-command -l" 
( pass -l as the "Lock" function. )

EDIT: When I put this in "Startup" in Sessions, it does not lock the screen, like it does when I run it through terminal, it just shows up in the process list.

This is what I intend to achieve.

Have ubuntu automatically login, then lock the computer, because I am the only user on the computer. ( Which makes the unattended boot much quicker. )

---

