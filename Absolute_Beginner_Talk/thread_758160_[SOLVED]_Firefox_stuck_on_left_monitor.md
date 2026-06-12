---
title: "[SOLVED] Firefox stuck on left monitor"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by myst1c on 2008-04-17
I have dual monitors, and the left monitor is smaller than the right. today, after returning from school, i opened up firefox. it opened in the left monitor(as opposed to opening in the right as it usually does)

the title bar is missing, and i can't move the window. I can minimize it using the taskbar, and unmaximize it, but it stays exactly the same. i've tried switching my default X screen to no avail, and have since switched it back.

can somebody please help me figure this out? it's annoying as hell

---

### Post by northern lights on 2008-04-17
Hold "Alt" right-click and drag to move the window

---

### Post by myst1c on 2008-04-17
didn't work... any other ideas? as i said, i don't have a title bar, and i can move it to a different workstation, but that's all

---

### Post by rune0077 on 2008-04-17
What happens when you right-click the window in the taskbar and select "Move"?

---

### Post by Linux_Man on 2008-04-17
Have you tried killing it with Xkill or restarting your computer or X? If you havn't press Alt+F2 and type in xkill and then hover that over the firefox window, that terminates the connection to the X server and usually closes the program, or fire up a terminal and type in killall firefox-bin (I think thats the right process, Bash can tab complete killalll). Or to kill the X server press CTRL+ALT+Backspace which will return you to the login screen and type in your login name and password and see if it works.

---

### Post by myst1c on 2008-04-17
i have no problem closing it or killing the process... i just want to be able to move it to the other monitor...

i have tried right clicking on the taskbar and using move, again to no avail...

also, it says i'm using gutsy, but i'm using hardy...

and rune, nice avatar

---

### Post by rune0077 on 2008-04-17
> **myst1c said:**
> 
and rune, nice avatar

Thanks.

Okay, now let's try a stupid solution which will be a pain if you have to do it every time, but just to see if we can move it at all. Make sure that expo is on in Compiz (I'm assuming you're using Compiz, otherwise ignore this post), then trigger it (expo - typically with Super+E). From the expo-preview thingy, try to see if you can drag the Firefox window to where you want it.

Another thing: can you move other Windows around just fine? Try to check in Compiz settings if the "Move Windows" is checked.

---

### Post by myst1c on 2008-04-17
not using compiz, but i do have visual effects on... anybody got aim? it'd help to figure this out if i could talk to you in real time... msn works too

---

### Post by rune0077 on 2008-04-17
Sorry, I have neither, but actually I just remembered that F11 toggles Firefox (and many other apps) between normal and fullscreen mode. Try hitting F11, I'm betting that should actually solve your problem.

---

### Post by myst1c on 2008-04-17
sir, you are amazing! thank you

---

### Post by rune0077 on 2008-04-17
Heh, sometimes the solution is so simple it's easy to miss it :)

Glad I could help.

---

