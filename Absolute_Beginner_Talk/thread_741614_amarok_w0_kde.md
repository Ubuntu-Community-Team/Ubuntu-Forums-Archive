---
title: "amarok w/0 kde"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-03-31
i have read through most of the gnome/amarok threads and none really answered my question... 

is it possible to have amarok in gnome without all the kde library stuff?... just the bare-bones program in gnome?  or should i just use something else... i would prefer to keep this thing 'lean'.. haha

---

### Post by privaterolf on 2008-03-31
I've always just used Add/Remove Programs to get it.

---

### Post by Oldsoldier2003 on 2008-03-31
> **manicmailman said:**
> i have read through most of the gnome/amarok threads and none really answered my question... 

is it possible to have amarok in gnome without all the kde library stuff?... just the bare-bones program in gnome?  or should i just use something else... i would prefer to keep this thing 'lean'.. haha

Amarok requires some Kde libraries in order to run. I believe that they are worth the small amount of space they take.

---

### Post by tubasoldier on 2008-03-31
If you have a newer computer (within the last few years) you shouldn't even notice the kde libraries being loaded. Amarok must have those to run as it was written with a different graphical api.

---

### Post by manicmailman on 2008-03-31
when i check it on the package manager it wants to install everything... like "kde desktop" n all that... is there a way to do it so that it d/ls the libraries but not all kde?

---

### Post by dr.silly on 2008-03-31
actually a pretty light program

---

### Post by tubasoldier on 2008-03-31
you should be able to install it without the kde-desktop meta package.

I would open a terminal and type in the following:
```
sudo apt-get install amarok
```

That way only the things you really need should be installed.

---

