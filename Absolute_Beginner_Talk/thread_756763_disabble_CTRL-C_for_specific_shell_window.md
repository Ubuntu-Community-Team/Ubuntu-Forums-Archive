---
title: "disabble CTRL-C for specific shell window"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by JoaoCarlosCorreia on 2008-04-16
Hi,
I have a script allways running in a Ubuntu but every now and then someone goes tehere and kills my console window.

Is there any way to disable CTRL-C for this specific window, or send some kind of warning, like "do you really want to close this window?"


Thanks in advance,


João Correia

---

### Post by Trail on 2008-04-16
I remember there was a wrapper utility that would execute an application while protecting it from signals (like Ctrl-C), but I can't seem to find it now... :(

However, I found the **trap** command. Take a look at the trap manual. It seems able to do what you are asking for (also the warning message).

Edit: If they are actually closing the window in which the script runs, i think the easier way to prevent this would be to run the script from, say, Ctrl-Alt-F5 or so, screen? No one would normally look there without reason :)

---

### Post by JoaoCarlosCorreia on 2008-04-16
thanks for your help trail!!!

Running in another screen will work just fine

hugs,

João Correia

---

