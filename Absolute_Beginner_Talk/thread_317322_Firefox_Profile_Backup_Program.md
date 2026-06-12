---
title: "Firefox Profile Backup Program"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-12-12
Is there a program such as MOZBACKUP that backs up the Firefox profile folder in another location for safe keeping in case the profile folder gets corrupted.  If there is nothing like this available would a script file work and if so how would one go about writing it.  Any help would be appreciated.

Donnie

---

### Post by xyz on 2006-12-12
In a terminal, this should do it:
```
cp -r /home/user/.mozilla /home/user/.mozilla-bkup
```
You may want to change the 2nd part of the command line to whatever_location you want.
Change "user"...of course.

---

