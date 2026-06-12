---
title: "Window Manager takes FOREVER to load!"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by BoyBlunder on 2006-09-10
I've recentely installed the xgl nvidia drivers and ever since, the Window Manager (shown on spash screen) takes forever to load (1+ minutes). Is this normal?

---

### Post by bulldog on 2006-09-10
I'm not sure what you mean.
Is that after booting or with booting.

When you turn on your computer and make your choice in grub you see Ubuntu booting up.
After a short periode of time  in which you see all the booting on your screen you get a black screen and after 2 seconds your login screen.

When showing your login screen takes a minute then there is definitly something wrong.

---

### Post by BoyBlunder on 2006-09-10
I've taken a screenshot of the "problem"

[http://img179.imageshack.us/my.php?image=windowmanagerqg9.png](http://img179.imageshack.us/my.php?image=windowmanagerqg9.png)

It hangs there for a minute, and then stuff in my task panel (battery icon, gDesklets) will all load at one time, and this is well after I'm already on, surfing the net, etc.

---

### Post by NiceGuy on 2006-09-10
I could be wrong but I think this might be the 'age old problem' of gnome's persistant splash screen. Can you do stuff whilst the splash screen is there? does clicking on it make it disappear?

---

### Post by BoyBlunder on 2006-09-10
yea, if I click on it, it disappears and I can easily work with the window up, but stuff like my Notifaction area, and gDesklets take forever to start.

---

### Post by NiceGuy on 2006-09-10
Ah, I suspect what you have there is actually 2 'bugs'. The spash screen taking ages to go is quite a common one and has been around for ages. It has something to do with having too many things loading at the start of the users session. The only fixs I know of is to a) disable the splash screen or b) change the order things load up in system > preferences > sessions > current session. 

I *think* that the problem is that everything that starts loading before the splash has to be loaded by the time the splash has finished its animation otherwise it sort of 'gets stuck' (but I could be wrong). 

If you increase the order of some 'non-essential' things (eg. gDesklets) to say... 60 or so, then that might solve that problem (It might not - you'll just have to have a play around I'm afraid).

As for the problem with gDesklets not starting... I suspect that is to do with xgl. I had a similar problem with logging out - try to log in then try to log out again, on my machine it takes AGES for the dialoge to come up.

Thinking about it... it might again be to do with the order things are loaded again...

Maybe try reducing the order of the gnomebar to 30 (in the hope of getting it loaded before some to the XGL stuff)?

Sorry I can't be more helpful, it'll probably be a bit of a case of trial and error. Post how you get on!

ps. don't forget that xgl etc. is VERY experimental at the mo, so expect a few bugs.

---

