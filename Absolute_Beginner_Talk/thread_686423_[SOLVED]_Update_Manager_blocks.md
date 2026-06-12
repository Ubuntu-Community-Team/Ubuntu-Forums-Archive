---
title: "[SOLVED] Update Manager blocks"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by lila on 2008-02-03
Hi, 
the update manager showed updates available,
I opened it and unclicked a few I didn't want (for programs I never use).  Clicked "install updates".  And Now it's grey and showing the little clock turning for over an hour.  I tried to close it, but it won't do that either.  It's not the first time, there's quite a few updates we ended up not doing because of this.  Very occasionally it works.  
Could this have anything to do with not enough RAM?  (256MB).  
We're thinking of installing Xubuntu for this reason.
Lila:confused:

---

### Post by RomeReactor on 2008-02-03
Hi. I don't think RAM is the issue here. Please open a terminal (Applications->Accessories->Terminal) and write or paste:
```
sudo aptitude update
```
then press enter. After that:
```
sudo aptitude safe-upgrade
```
If error messages appear in the terminal, please post them.

---

### Post by lila on 2008-02-03
Wow, that not only worked, but worked in under 15 minutes!  Normally, if and when the update manager works, it takes well over an hour!
Here I was, thinking I had time to clean the kitchen... ah well, I'm not complaining!:lolflag: Thanks a lot, I'll keep that thread in my "How to Ubuntu" file.
Lila

---

