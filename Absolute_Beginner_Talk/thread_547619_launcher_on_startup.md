---
title: "launcher on startup ?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by fenier_wolf on 2007-09-10
hi guys thanks for reading my post, launcher creates an error after Gnome loads.  After the normal start up process i get a laucher error saying "Could not lauch application, not a lauchable item"

I was a lifetime windows user so i have no idea on how to troubleshoot this error,  ive tried the sticky guide in this section but i still need to be around linux a little while longer to even know what to be looking for.    I just want to find out what launcher is trying to run, and figure out what to do from there.

dont leave me hanging

peace

---

### Post by por100pre1 on 2007-09-10
Can you please tell us which application is not launching?

---

### Post by ubuntukerala1980 on 2007-09-10
In gnome
System -> Preferences -> Session 
Find which applications in your startup
I think some of this applications are causing problem but am not sure
Try to login using failsafe gnome

---

### Post by BrendanM on 2007-09-10
I don't think he knows. IIRC, Launcher is responsible for the "quick-launch" (windows terminology) icons to the right of the "System" menu.

By default, I think the three apps there are Firefox, Evolution Email Client, and a Help icon.

fenier_wolf, can you tell us how many icons you see there? If one of them is missing, that's probably where the error is coming from.

---

### Post by fenier_wolf on 2007-09-10
ive removed the help icon and added gain instead, all 3 are there.  under sessions in the Start up Programs tab > beryl manager, evolution Alarm notifier, network man, power man, resticted drivers man, update notifer, volume manager
  current session tab i have 3 programs that  have a (?) icon instead of Cogs.

am i on the right track?

---

### Post by BrendanM on 2007-09-10
Sounds like it. I'm not sure whether a ? icon is bad or not. The other thing you could try doing is after you see the error message pop up, press ctrl+alt+F1, which will drop you into a terminal that might show more detailed error information. You can press crtl+alt+F7 to switch back to the GUI.

In any case, this doesn't sound like a critical error. Annoying, obviously, but I wouldn't worry too much.

---

### Post by fenier_wolf on 2007-09-10
failsafe gnome produced the same error.
i guess its a problem with GNOME?

---

### Post by BrendanM on 2007-09-10
You could do some A/B testing unchecking items from the startup programs list, and see if you get any better luck. Also google/search the forums with the exact text of the error message and see if anyone else has had this issue.

---

### Post by fenier_wolf on 2007-09-10
fixed, it was a dead link.  thanks alot you guys, this was really fast.  I love this OS more and more every minute.
Before i go any quick suggestions for someone migrating from xp to linux/ubuntu, i already have beryl installed for some eyecandy, anything else i can do to make my MSfriends green with envy?

---

