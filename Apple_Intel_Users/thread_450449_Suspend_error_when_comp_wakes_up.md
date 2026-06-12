---
title: "Suspend error when comp wakes up"
date: 2007-05-21
forum: Apple Intel Users
---

### Post by bendrops on 2007-05-21
Yo, I'm getting a suspend error when the computer wakes up from it 
But it seems like the suspend is working , so I'm just getting a false error. 
Anyone knows how to fix this?

---

### Post by ronocdh on 2007-05-21
> **bendrops said:**
> Yo, I'm getting a suspend error when the computer wakes up from it 
But it seems like the suspend is working , so I'm just getting a false error. 
Anyone knows how to fix this?
Please transcribe the error verbatim so we know what we're working with. Also, how is suspend "working" if you're getting an error?

---

### Post by bendrops on 2007-05-21
well, everything seems to work fine. The screen turns black, the hard disk stops working (I can feel it stopped) and when I lift my screen back up the computer wakes up, I'm in my screen saver. It asks for the password, I punch it in and I get this error (In a little yellow ballon):

Suspend Problem
Your computer failed to suspend
Check the help file for common problems

---

### Post by benanzo on 2007-05-21
I've had plenty of suspend errors in my day, and never have they been so nice as to actually tell me in a dialog that there was an error.  Normally they just force me to cold-boot.
To get some more info about the error, try suspending, then waking up and do:

```
dmesg | tail
```

That should print what specific device (if any) had a problem.

---

