---
title: "boot.local equivalent?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by sp00ki on 2006-07-27
Hi
I just set up a new install of ubuntu, and i'm in the middle of my typical post-install routine, but i've run into a little issue... i can't seem to find the file "boot.local".
there are a few commands i'd like to run during boot (off the bat before i get to the desktop), and i was expecting to put them in /etc/init.d/boot.local, but i can't seem to locate the file.
in searching the forum, i've found that others have asked the same question, but were always given "alternatives" to what it is they wanted to do, rather than an answer to what ubuntu's boot.local equivalent is.
any insight?
thanks!

---

### Post by taurus on 2006-07-27
Well, there is /etc/init.d/rc.local.

---

### Post by sp00ki on 2006-07-27
Thanks.
How should one handle the "exit 0" line in this file?
I'm not familiar with it...

---

