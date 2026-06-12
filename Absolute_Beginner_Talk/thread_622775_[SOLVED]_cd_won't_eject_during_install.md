---
title: "[SOLVED] cd won't eject during install"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by juniah on 2007-11-25
Im trying to install a game via wine and I need to install the second CD but it wont let me eject the first.  The error I get is that a program is using it.  Any ideas?

---

### Post by CatKiller on 2007-11-25
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

> # Never run an install from the CD directory - Don't change directories to the CD drive in order to launch a setup executable. Doing so can sometimes prevent your CD drive from properly ejecting when you need to swap install CDs. Instead launch the install by running this from your home directory:

```
wine /media/cdrom0/setup.exe
```

# "wine eject" is your friend - If an install needs you to switch CDs and the OS complains that you can't eject the CD, then open a new terminal window and run:

```
wine eject d:
```



---

### Post by ericartman on 2007-11-25
Nevermind

Cart

---

### Post by juniah on 2007-11-25
Thanks guys!

---

### Post by juniah on 2007-11-25
Another problem, the installer will only recognize the path for the first CD and not the second CD which is the same as the first.  Ugh.

---

### Post by baqai on 2007-11-25
i found out a way to solve this, its not the best way around and its not guranted to work all the time,

Dump the contents of both the cd in a directory and run setup from there, i was having problems with Swat 4 and i managed to get it install that way, hope that helps

---

### Post by juniah on 2007-11-25
Also I forgot to note that it skips the want for CD2 and moves to CD3, when CD3 is not needed.

---

### Post by juniah on 2007-11-25
baqai I'll give that a shot.  Sorry I didnt refresh before posting about the CD3 issue

---

### Post by juniah on 2007-11-25
Ok, I was able to solve the problem.

My friends computer couldn't recognize the original CD (windows - wtf?), so I grabbed the original CD and it worked fine.

Thanks for all the help!

---

