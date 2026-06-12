---
title: "Desktop Bigger than my screen"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by pizzutz on 2007-01-21
I've been messing around with some programming projects and some video games through wine.  Sometimes when these quit, they leave my desktop such that the desktop size is correctly left at 1400x1050, but I can only see 640x480 of it at a time.  I can use the whole desktop, my "window" onto it follows my mouse around, but I'm basically zoomed in on a part of my desktop.  Can someone tell me of an easy way to reset this when it happens?  Currently, I am just restarting the xorg with ctrl-alt-backspace. Is there an easier way?

---

### Post by crane on 2007-01-21
You can use the menus.
System>preferences>screen resolution.
Then select a different res change it, select no when asked do you want to kept the new resolution. It should return you back to the correct one.

I believe this issue can be corrected by some settings in Xorg. Are you running the program in Wine at a different res?
If not I believe you can remove all the resolution settings that you do not use and it will default back to the correct setting.
I am not 100% sure about that though so do a little research before changing.

Good Luck!

---

### Post by pizzutz on 2007-01-21
I had already tried using screen resolution to reset it, it still reverts back to the zoomed in desktop.  

I'm messing with GLUT and OpenGL, so something isn't closing right in the programs.  I'll just have to figure out what it is and write my own program to correct it.  I was hoping there was some magical screen reset button I could press to fix it while I'm trying to figure out what the problem is, but it's no big deal either way.

Thanks for trying!

---

