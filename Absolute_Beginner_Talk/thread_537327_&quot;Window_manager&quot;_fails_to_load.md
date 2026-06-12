---
title: "&quot;Window manager&quot; fails to load"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by scott.todd on 2007-08-28
I have the save session option turned on, and when mplayer crashed I restarted the system so it would behave again (logging in and out didn't work).  When the system restarted, my window manager failed to load and I am missing the borders and title bars of all my windows making it very hard to do anything with the windows, even the task bar doesn't work properly.  Fortunately, it only affect my user and I am able to log in as a different user so I can write this post.
   
Help is greatly appreciated.  I expect that there is a text config file somewhere that I can edit to resolve this?

---

### Post by SunnyRabbiera on 2007-08-28
hmm, what window manager do you use?

---

### Post by scott.todd on 2007-08-28
beats me, just a regular Ubuntu Feisty install,  so is it gnome?  btw, gnome sure looks/works funny without this "window manager"...  no idea what to do

---

### Post by irish_flu on 2007-08-28
I don't have any suggestions for you at the moment, but your Window Manager (the default Ubuntu one, anyway) is called "Metacity".

Maybe you can start it from the command line and see what happens....

---

### Post by scott.todd on 2007-08-28
dumb question alert:
do I just type "metacity" ??

---

### Post by irish_flu on 2007-08-28
*shrugs* I'm not really sure.  That's certainly worth a shot.

---

### Post by scott.todd on 2007-08-28
> **scott.todd said:**
> dumb question alert:
do I just type "metacity" ??

I can answer it now:  and the answer is YES!!   Now to find out if it sticks and I will update everyone (who cares to know)...

---

### Post by scott.todd on 2007-08-28
> **scott.todd said:**
> I can answer it now:  and the answer is YES!!   Now to find out if it sticks and I will update everyone (who cares to know)...

logged out and back in and...
   
WOOHOO!!  chalk that up as another issue resolved,  thanks a bunch!!

---

### Post by SunnyRabbiera on 2007-08-28
a re install of metacity might help if this crops up again

---

### Post by DarkN00b on 2007-08-28
Looks like Metacity crashed and when you restarted, the session was saved -- without Metacity running. When you logged back in the session manager looked at the saved session and *didn't* start Metacity because you shut down without Metacity running. Does that make sense?

So when you started Metacity and rebooted, the session was saved and Metacity started as usual, because the previous session had ended with it running.

Sometimes I'm so bad at explaining things... :D

---

