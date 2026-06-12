---
title: "[SOLVED] Synaptic manager error"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-12-10
I was trying to correct my flash problem and now its gotten even worse, during the installation of Ubuntu restricted extras Synaptic froze, and i closed it now when i restarted the system it gives me this very scary messege

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Jesus christ what do i do ?

---

### Post by v.alari on 2007-12-10
Try
Applications -> Accessories -> Terminal

Script

sudo dpkg --configure -a

EDIT:
use the sudo command with care though but that command should restruction the packages properly (or something like that) if you get another error sort of like this
dpkg: parse error, in file `/var/lib/dpkg/updates/0024' near line 24 package `dbus-1':
EOF during value of field `Description' (missing final newline)
you will have to run another command

---

### Post by Taras on 2007-12-10
Oh yeah its begun to count something, thank you, i am so stupid

---

### Post by v.alari on 2007-12-10
Dude your posting in that Absolute Beginner Talk forum. Your not stupid, your inexperienced or new, like me, play with it a bit. Im fortunate enough to have a machine I can completely screw up and not care except for the time it took to set it up. If that isnt the case with you, you can still play with it just move a little slower and remember the boards and google are your friends.

---

### Post by HELBO on 2007-12-12
Got the same problem.

And when I run the: dpkg --configure -a

I got the : dpkg: parse error, in file `/var/lib/dpkg/updates/0007' near line 18:
 missing package name

What do I do then ?

---

