---
title: "Can I use wildcards in a tar exclude command?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-09
I want to use Heliode's method of making a system backup.

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I want to exclude ./trash, ./trash-root, ./trash-dace, and all subdirectories or files therein.  And I want them to be excluded in /home, and two other hdd's.  How do I do this?

---

### Post by ICUR2Ys on 2007-06-10
Never mind.   I figured out how to do it.   This thread is done.

---

