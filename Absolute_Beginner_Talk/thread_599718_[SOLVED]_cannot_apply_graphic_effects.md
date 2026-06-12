---
title: "[SOLVED] cannot apply graphic effects"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-01
I get an error when I try to set graphics effects to normal.

My Graphics card is set up right, I am using dual monitors and everything is fine.  Wierd problem

---

### Post by nike984 on 2007-11-01
are you using intel integrated card?
there are some graphic cards that are blacklisted,
so, if you are one of those cases, you wouldn't be able to use 
visual effect unless you change the blacklist file manually.

---

### Post by Tdukes on 2007-11-01
Im using an Nvidia Geforce 7800

---

### Post by Tdukes on 2007-11-01
I hate to do it

Bump

---

### Post by Tdukes on 2007-11-02
Ok, I figured it out.....maybe this will help someone else out

I couldnt get the effects to work when in Multi desktop mode.

I installed compfiz and set my mode to twin mode instead of xinerama.  then after reloading X I opened the terminal and typed compfiz -restart

all works now

---

