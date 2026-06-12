---
title: "Sharing files between Windows and Linux on seperate partitons"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-21
I read the wiki  and installed the ntfs config software it works great. I installed the windows software 
on my XP partion to do the opposite, and when I double click drive L (wich is what I named the Linux partion on my windows device manager) it tells me that it's not formated and that it wants to erase it. Any Ideas? Or some other way to mount Linux partition automaticly when I boot Windows

---

### Post by Hobo Joe on 2007-08-21
Did you install FSdriver?

[www.fs-driver.org](www.fs-driver.org)

---

### Post by swoll1980 on 2007-08-21
> **Hobo Joe said:**
> Did you install FSdriver?

[www.fs-driver.org](www.fs-driver.org)

Yes and when I click on drive L it tells me it's not formatted.

---

### Post by swoll1980 on 2007-08-21
I figured it out. I'm using Freespire 2.0 it has a reiserfs file system is there a driver for that?

---

### Post by testube_babies on 2007-08-21
I think the project is dead...
[http://rfsd.sourceforge.net/](http://rfsd.sourceforge.net/)

---

### Post by swoll1980 on 2007-08-21
yeah it's as dead as disco

---

### Post by swoll1980 on 2007-08-21
is there a way to change it to ext 3

---

### Post by Tyke91 on 2007-08-21
to do that you'd need to reformat your hard drive with something like Gparted

---

### Post by swoll1980 on 2007-08-21
will that erase my stuff?  Can I make a home partition that they both can read/write on? IS there a format they both understand?

---

