---
title: "ok so I got the awn dock but not the manager...some help please!"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by virologynerd on 2008-02-22
ok so i finally got beryl working (i still can't get the cube, but that can wait) and i installed AWN dock via terminal (where i tend to copy and hit enter aimlessly hoping something is going to strike/work) but I think i messed up (shocker) somehow i managed to not install the awn dock manger. so if someone who actually knows what their doing (unlike me:confused:) could help, that would be much appreciated!!!!!

---

### Post by glennric on 2008-02-22
How are you trying to install awn?  Do you have debs, are you trying to install from a repository, or are you trying to compile awn yourself?

By the way, when you say you got beryl working, did you mean compiz?  If you are seriously trying to install beryl, stop.  Beryl is out of date and you should install compiz instead.  It is in the repositories.

---

### Post by virologynerd on 2008-02-22
ok thanks, umm when i tried installing with the instructions from the wiki article, i am not sure how (sorry, i am really clueless) I just copied code from the instructions and entered them in the terminal, I am VERY new to ubuntu, way more familiar w/ mac.

thanks for the advice on beryl it has been giving me LOADS of problems!

---

### Post by glennric on 2008-02-23
The easiest way to install awn is to enable the gutsy-backports repository and do
```
sudo apt-get install avant-window-navigator awn-manager
```
or use synaptic.
By the way, there is a newer version of compiz in the gutsy-backports repository.

---

