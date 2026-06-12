---
title: "bin/bash permission denied"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by sciencectn on 2008-04-09
I was changing file permissions on a few things, and I accidentally used the --recursive option with chmod in the completely wrong directory. I held up on the arrow key to get to a command a recently entered and meant to select the command saying "sudo chmod -R 755" but I accidentally chose "sudo chmod -R 666". Now when I try opening a terminal the windows stays open for a split second and then closes. I go to a virtual terminal with ctrl+alt+f1 and try to log in, and it says "/bin/bash cannot be executed, permission denied". Obviously I need to restore file permissions on /bin/bash but I can't get into a terminal to do it.

---

### Post by Oldsoldier2003 on 2008-04-09
> **sciencectn said:**
> I was changing file permissions on a few things, and I accidentally used the --recursive option with chmod in the completely wrong directory. I held up on the arrow key to get to a command a recently entered and meant to select the command saying "sudo chmod -R 755" but I accidentally chose "sudo chmod -R 666". Now when I try opening a terminal the windows stays open for a split second and then closes. I go to a virtual terminal with ctrl+alt+f1 and try to log in, and it says "/bin/bash cannot be executed, permission denied". Obviously I need to restore file permissions on /bin/bash but I can't get into a terminal to do it.

depending on where you did the recursive chmod it may not be feasible to properly restore permissions. do you remember the exact command and path? If you executed it in the root you are just better of backing up your data and reinstalling.

---

### Post by sciencectn on 2008-04-10
I think it only did /bin and everything inside it.

What I'm going to try now is live booting the ubuntu CD and seeing if that will change permissions. If that doesn't work, I'll have to use a recovery CD.

---

### Post by PhilJ on 2008-04-10
have you tried opening the dir in nautilus and altering the permissions from there?
can you run nautilus as root?

P

---

