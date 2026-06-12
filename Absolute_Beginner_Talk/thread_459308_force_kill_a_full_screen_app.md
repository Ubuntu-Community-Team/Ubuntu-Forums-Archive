---
title: "force kill a full screen app"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by xtang on 2007-05-30
for an app thats hogging the whole screen (like a game), how do i force kill it? i cant seem to use xkill (even though i can see the mouse cursor with that skull, clicking doesnt do anything)

---

### Post by daimaru on 2007-05-30
if you can open terminal enter 
```
ps -aux
```

find the apps processId and type 
```
kill -15 processID
```
or kill -9 processID whichever works .

---

### Post by aysiu on 2007-05-30
Press Control-Alt-F1

Log in

Type ```
top
``` Find the name of the program running. Press Q. Type ```
killall *programname*
``` Press Control-Alt-F7. Hopefully, it's killed.

---

### Post by oilchangeguy on 2007-05-30
> **xtang said:**
> for an app thats hogging the whole screen (like a game), how do i force kill it? i cant seem to use xkill (even though i can see the mouse cursor with that skull, clicking doesnt do anything)

try right clicking the top/bottom panel, click add to panel, locate force kill and add that to the panel. then use that to kill the problem app.

---

### Post by aysiu on 2007-05-30
> **oilchangeguy said:**
> try right clicking the top/bottom panel, click add to panel, locate force kill and add that to the panel. then use that to kill the problem app.
Isn't that the same as using *xkill*?

---

### Post by oilchangeguy on 2007-05-30
> **aysiu said:**
> Isn't that the same as using *xkill*?

but once it's added to the panel, it'll be faster than using xkill. no need to open a terminal.

---

### Post by aysiu on 2007-05-30
> **oilchangeguy said:**
> but once it's added to the panel, it'll be faster than using xkill. no need to open a terminal.
But the OP said *xkill* didn't work, so speed isn't the issue here.

---

### Post by aysiu on 2007-05-30
> **oilchangeguy said:**
> but once it's added to the panel, it'll be faster than using xkill. no need to open a terminal.
Speed isn't the issue. The OP said *xkill* didn't solve the problem.

---

### Post by oilchangeguy on 2007-05-30
> **aysiu said:**
> But the OP said *xkill* didn't work, so speed isn't the issue here.

the user said "i can't seem to use xkill" not it didn't work. anyway if you can't stop a problem app, the computers power button works real well for this type of thing. press it until the computer turns off, and reboot. problem should be gone.

---

### Post by aysiu on 2007-05-30
> **oilchangeguy said:**
> the user said "i can't seem to use xkill" not it didn't work. Well, no. The OP said > i cant seem to use xkill (even though i can see the mouse cursor with that skull, **clicking doesnt do anything**) So *xkill* did not work.

---

### Post by dministrator on 2007-12-02
I'm also facing this same problem. I accidentally made xclock full screen and left click, right click, double click anywhere, at the top, bottom, left or right.... none of that worked. I had to restart the computer. Will the solution with Ctrl-Alt-F1 / killall technique work in this case as well if it happens again?

---

