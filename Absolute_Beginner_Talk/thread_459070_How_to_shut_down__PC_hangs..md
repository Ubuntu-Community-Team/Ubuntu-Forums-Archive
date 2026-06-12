---
title: "How to shut down?  PC hangs."
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-05-30
Ubuntu FF i386 hangs at a splash screen when asked to shut down.  Does not respond to any keyboard commands.  I hunted a half hour before asking...

This is a two part question:

How to get it to shut all the way down?

When one has a splash screen, is there a command that will bring the system back up?

---

### Post by justifier on 2007-05-30
unplug it? last resort on hang.

try shutting down from the terminal with 

sudo shutdown now

does this work?

---

### Post by Crafty Kisses on 2007-05-30
> **bettyhills said:**
> Ubuntu FF i386 hangs at a splash screen when asked to shut down.  Does not respond to any keyboard commands.  I hunted a half hour before asking...

This is a two part question:

How to get it to shut all the way down?

When one has a splash screen, is there a command that will bring the system back up?

When this hang happens, you should try and press:
```
Ctrl+Alt+F2
```
You should go to a "DOS" looking screen and then after that type:
```
sudo shutdown -r now
```
That should shut it down for you. :D

---

