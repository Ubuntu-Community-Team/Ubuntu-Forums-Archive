---
title: "[SOLVED] title bar missing termal window is white"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by chach man on 2008-01-17
close minimize maximize/restore buttons are all missing from the title bar. 
my terminal is entirely white. 

I'm not running anything fancy just the original GUI.

---

### Post by spiderbatdad on 2008-01-17
try this ```
metacity --replace
```

---

### Post by chach man on 2008-01-17
um... not that i can tell I cant see if the terminal window is accepting my input.
I typed in sudo <enter> <the root password> sudo metacity --replace

It's been a while since i had to do stuff in the terminal tell me if im typing stuff in wrong

in windows you can restore the system is there something like that for ubuntu?

---

### Post by nikoPSK on 2008-01-17
you can restore xorg and others? Do you want to reconfigure xorg?

---

### Post by p_quarles on 2008-01-17
You don't need to use sudo with that command. Just type it in the terminal. 

If that doesn't do anything, what happens when you try to run an app from the terminal? E.g,
```
xterm
```

---

### Post by voteforpedro36 on 2008-01-17
Try pressing Alt and F2, which should bring up a Run... menu. Type metacity --replace from there.

---

### Post by spiderbatdad on 2008-01-17
try alt-f2 and enter metacity --replace

---

### Post by chach man on 2008-01-17
Thank you its working now

---

### Post by voteforpedro36 on 2008-01-17
If you don't care, go to Thread Tools (on this forum by your first post) and Mark Thread Solved?

Glad you got it working.

---

### Post by nikoPSK on 2008-01-17
> **voteforpedro36 said:**
> If you don't care, go to Thread Tools (on this forum by your first post) and Mark Thread Solved?

Glad you got it working.

Like this:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

---

