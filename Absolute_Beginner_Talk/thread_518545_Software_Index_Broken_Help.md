---
title: "Software Index Broken Help?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by thavok on 2007-08-06
just got this error first time linux user here help?

ryan@ryan-desktop:~$ sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ryan@ryan-desktop:~$

---

### Post by alienexplorers on 2007-08-06
You need to run in terminal
> sudo dpkg --configure -a

---

### Post by thavok on 2007-08-06
thanks much i was missing the sudo part i take it that basically requests putting you in a super user state?

---

