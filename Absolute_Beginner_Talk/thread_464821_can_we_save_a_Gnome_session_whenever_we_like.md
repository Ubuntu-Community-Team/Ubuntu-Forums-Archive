---
title: "can we save a Gnome session whenever we like?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-05
Hi
Thank you for reading my post
is it possible to save a GNOME session when ever we want and then recover to that session without shutdown?


for example an application take a complete snapshot of memory and then recover it ...

Thanks

---

### Post by frodon on 2007-06-05
To manually save the gnome session open a terminal and type :
```
gnome-session-save
```

---

### Post by Rui Pais on 2007-06-05
i wonder if legolas_w are thinking of something like suspend-to-rom...
he/she mentions a "complete snapshot of memory" and close a session but without shutdown...

---

### Post by legolas_w on 2007-06-05
How i can restore the session after i saved it?
I execute that command and it did nothing, even i typed some characters after i execute the command in terminal and finally i killed the terminal session.



Indeed I want to save session manullay to be able to restore it when my computer crashed or i lost power.
this way i can start ubuntu and then I can restore the session.

All application will become open again, my music playing, ....



Thanks

---

### Post by Rui Pais on 2007-06-05
> **legolas_w said:**
> How i can restore the session after i saved it?
I execute that command and it did nothing, even i typed some characters after i execute the command in terminal and finally i killed the terminal session.



Indeed I want to save session manullay to be able to restore it when my computer crashed or i lost power.
this way i can start ubuntu and then I can restore the session.

All application will become open again, my music playing, ....



Thanks

if you save your session with gnome-session-save it will be restored next time you login again, from crash or not.
I don't know if it's possible to load a specific session saved that way... and most certain not from an already running session. 

Thats a strange request... did your computer crash that many times? Anyway as soon as you reboot and login again your session will be what is saved (some apps may be fail from being saved, but they are exceptions...)  

You can too, set gnome login manager to automatically load a user so it will directed send user (you) for gnome session.

Or you can use Suspend (when you press the button to Exit it should give that option) that saves your running sessions to RAM and turn poweroff and restore everything in seconds when you turn it on again.

---

