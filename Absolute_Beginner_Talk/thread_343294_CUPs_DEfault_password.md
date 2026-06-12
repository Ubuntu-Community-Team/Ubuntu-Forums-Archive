---
title: "CUPs DEfault password"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-01-21
I am using CUPS and kubuntu dapper, Am trying to install my printer but it wont let me, asks for user and password, I have tried my username and password and root and password but it doesnt let me in.

What do I need to do?

---

### Post by Joeb on 2007-01-22
> **tommy1987 said:**
> I am using CUPS and kubuntu dapper, Am trying to install my printer but it wont let me, asks for user and password, I have tried my username and password and root and password but it doesnt let me in.

What do I need to do?

Since by default Kubuntu has the root account disabled, there isn't a root password to enter for Cups.  The easy thing to do is to add the printer using the KDE printer configuration tool (or Gnome's if you were running Gnome).  Otherwise, you can enable the root id and password, but since the KDE printer configuration is a front-end for Cups, that seems like overkill.

EDIT:  If you don't want to enable the root account but still want to use the webadmin interface, check out this thread: [http://www.ubuntuforums.org/showthread.php?t=304320&highlight=cupsys+shadow](http://www.ubuntuforums.org/showthread.php?t=304320&highlight=cupsys+shadow)

---

