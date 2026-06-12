---
title: "big problem, computer over, need help  screwed up everything"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by 005david on 2007-09-28
i think i have deleted my operating system or something...

i restarted and instead of the login screen, i got a terminal.  help??

---

### Post by wormser on 2007-09-28
It does not sound like you deleted the operating system.  For some reason X windows is not starting.  Can you give us more information about what you did before this problem started?  Try the following command to start X windows.

```
startx
```

---

### Post by 005david on 2007-09-28
idk, lots of things.  i installed ubuntu 7.04, tried to install beryl, diddn't work, tried to install compiz fusion, diddn't work, but the computer worked fine, it was just getting slow so i restarted it.

and the results of that "startx" thing weren't great, it just made the terminal smaller.

---

### Post by 005david on 2007-09-28
entered in the small terminal, and it said something like this:

X: user not authorized to use the X server, aborting.
xinit: Server error.

---

### Post by wormser on 2007-09-28
> **005david said:**
> entered in the small terminal, and it said something like this:

X: user not authorized to use the X server, aborting.
xinit: Server error.

I think this is a permissions error.  This [thread]("http://ubuntuforums.org/showthread.php?t=63096") looks like it can help you solve it.  Just use remember to use sudo before the commands.

Good luck.

---

