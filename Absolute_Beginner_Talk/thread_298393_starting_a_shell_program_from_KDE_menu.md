---
title: "starting a shell program from KDE menu"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by niki001 on 2006-11-12
Hi all,

One small problem. Hopefully somebody can help me out.
I've got a prog that runs fine whenever I start it from a terminal (non - root).
However I'm trying to get it started from KDE menu, without any luck so far.
I've tried severall options in KDE menu editor. Can anybody tell me what command to use to get it working. 
For now the only thing that happens is that the terminal pops up briefly and thats it...

thx for the help.

---

### Post by qpieus on 2006-11-12
Try putting ```
--noclose
```in the box next to "Terminal options"
Also check the "Run in terminal" box.

See attached photo.
I set up a little test script with the options mentioned above, and the script ran and the terminal window stayed open.

---

### Post by niki001 on 2006-11-13
> **qpieus said:**
> Try putting ```
--noclose
```in the box next to "Terminal options"
Also check the "Run in terminal" box.

See attached photo.
I set up a little test script with the options mentioned above, and the script ran and the terminal window stayed open.
Thx qpieus,

the '--noclose' option helped me, however most of the problems came because i hadn't used my full path. Apparantly my PATH didn't include the one where my program was placed. Now I got the program up and running through my KDE -menu. 
thx again

---

### Post by qpieus on 2006-11-13
You're welcome. I'm glad you got it working.

---

