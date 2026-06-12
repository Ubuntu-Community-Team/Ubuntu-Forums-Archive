---
title: "A little wacom help please...."
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by shadowfist on 2006-07-22
I am a very fresh Linux user and i have been playing around on my desktop with ubuntu.

and it works great but...
I have a graphire 3 wacom tablet and ubuntu recognises it just fine (shows up as a grapire 3 in the device manager)
but I dont see anyway to change the options of the tablet. (in windows for example I have it so that the mouse is used in "mouse mode" and the pen in "pen mode". "Pen" being absolute pointer movement and "mouse" being relative pointer movement.

am i missing something or is there some other way that i have to configure these?

also the mouse when it is in absolute pointer mode it seems to "de-calibrate" and i will find myself not able to get to one side of the screen untill i move the mouse to the extreme other side and then back again.

any ideas?

---

### Post by capi on 2006-07-23
in /etc/X11/xorg.conf under the input devices for Wacom you can add the lines

Option "Mode" "Absolute"

and

Option "Mode" "Relative"

under the stylus and mouse sections. Don't know if that helps. :D

---

### Post by shadowfist on 2006-07-24
hmmm... that didnt seem to have any effect...
thanks though!

any other ideas?

---

### Post by linear on 2006-07-24
Read [this thread]("http://www.ubuntuforums.org/showthread.php?t=25151"). It should help get you going.

---

