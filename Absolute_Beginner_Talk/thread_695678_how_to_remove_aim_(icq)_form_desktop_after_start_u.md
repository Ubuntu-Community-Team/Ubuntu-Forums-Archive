---
title: "how to remove aim (icq) form desktop after start up"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by chuffsy on 2008-02-13
Hello All , Im new to this forum  and ubuntu, and so far It seems to be the place to be for a totally new experience! I am running windows xp as well on the same computer. A friend of mine installed ubuntu and when he did my son did a (Aim/Icq) thingy and so every time I boot ubuntu This Big "pop up" of aim/icq shows on the desk top and i have to X it out..Just a minor nuissance but still I would like to delete the event as my son does not use it at all. How can i do this? Thanks in advance...chuffsy

---

### Post by kostkon on 2008-02-13
From your description I couldn't really understand which application may do this (maybe it's *Kopete*). Nevertheless, go to *System -> Preferences -> Sessions* and try to find it there in the list of applications. If it exists there, just remove it and it will stop loading everytime you login to your desktop.

---

### Post by jan quark on 2008-02-13
you can see what processes are running with this commadn
```

ps -A
```

if you recognize somehing similar to your problem 
you can manually stop the process from loading as
kostkon has explained it

---

### Post by Therion on 2008-02-13
Allow the annoying application to open, or open it yourself, and check for something like an "Options" menu or a "Preferences" option in the Edit menu.  What you're looking for is an option that says something along the lines of "Start this application every time the PC boots".  

The wording will vary, but you'll know it when you see it.  Uncheck or de-select that option and close the application.  Problem solved.

---

### Post by chuffsy on 2008-02-13
I found the pop up page under ..K menu..internet..I right clicked it and then deleted..now its gone...somehow I could not do the...system...preferences..sessions ..as recommended..I just didnt see preferences at all...ah well at least I  got rid of the aim/icq thingy..Thanks all !!!!

---

### Post by chuffsy on 2008-02-13
Spoke too early..Now its worse!! I restarted the computer and rather than only one window for the "aim/icq" thingy..it wants a password entry...nowIhave four of them. !..yikes ..what did I do ???? By the way the top of the box says ..GAIM... Im gonna poke around some more..Any ideas?

---

### Post by chuffsy on 2008-02-13
Talk about me being a novice at this thing ! Well I poked around alright and I happened to see the GNAIM characters on the "task bar". I basically cancelled these and did a restart and the entire episode did not happenr...is it time to celebrate?

---

