---
title: "yea stupid error i need help"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by i_are_dylan on 2008-04-09
yea i get a dumb error when i try and get updates for anything or try and install stuff or get stuff in the add/remove thingy it is like
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

could some one please help me

---

### Post by Tatty on 2008-04-09
The answer is right before you ;)

open a terminal (Applications->Acessories->Terminal) and run: ```
sudo dpkg --configure -a
```

At some point a package has failed to install properly, so you need to tell it to complete the installation fo that before you can install/remove anything else

---

### Post by i_are_dylan on 2008-04-09
mm kay thanks i was getting frustrated
i was like how did i screw up ubuntu in under a week of having it

---

### Post by Tatty on 2008-04-09
> **i_are_dylan said:**
> mm kay thanks i was getting frustrated
i was like how did i screw up ubuntu in under a week of having it

Dont worry, breaking ubuntu is a pretty common thing to do if you are new to linux.  The chances are that your first few weeks with it are going to be a little frustrating and plagued with breakages as you get to grips with it.

But trust me, this is a good thing.  Breaking something and then fixing it is the best way to learn how it works...  :)

---

