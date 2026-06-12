---
title: "cfdisk problem"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-27
Hi everybody.

Runnging cfdisk fromterminal I got this message:

FATAL ERROR: Cannot open disk drive
                          Press any key to exit cfdisk

:confused: 


Any hint, plese? thanks

---

### Post by xyz on 2006-12-27
What was the exact command you ran?

---

### Post by helphope on 2006-12-27
Sorry. Even if it has been six months by now I'm using dapper ...](*,) 
I got it:
I need to write ```
sudo cfdisk
```
not just
```
cfdisk
```
If I can add one more question: I've got one hard disk with the following partitions
```
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    74943224    37471581   83  Linux
/dev/hda2        74943225    78172289     1614532+   5  Extended
/dev/hda5        74943288    78172289     1614501   82  Linux swap / Solaris
```

Now I'd like to add one more partition just using cfdisk. (hda2 is the same as hda5, since its the swap partition)
Has anyone any hint or suggestion? Thanks

---

### Post by xyz on 2006-12-27
What do you want to achieve?
```
man cfdisk
```is quite helpful.

PS: May I suggest you don't ask 2 different questions using the same thread? It's hard to get helped that way and it also prevents others who might have a similar pbm to read on it.

---

### Post by helphope on 2006-12-27
> PS: May I suggest you don't ask 2 different questions using the same thread? It's hard to get helped that way and it also prevents others who might have a similar pbm to read on it.

Sorry. You are right.
You know, the questions bunch up together like cherries in a basket

:)

---

