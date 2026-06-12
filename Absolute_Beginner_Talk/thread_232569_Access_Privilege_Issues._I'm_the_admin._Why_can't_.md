---
title: "Access Privilege Issues. I'm the admin. Why can't I copy folders?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by fuzzybabybunny on 2006-08-08
I'm a first time Linux user and I'm kinda confused.

A week ago I could copy files, make folders, do all the basic admin stuff in Ubuntu, but now all of a sudden I can't. I keep getting the error "You do not have permissions to write to this folder" or somesuch.

Under users and groups I'm under the Admin group. Why would it suddenly decide to lock me out?

---

### Post by hopstah on 2006-08-08
even though you're in the admin group, you're not by default given admin priveledges all of the time.  you need to tell the computer that you want to do something as an admin.  you can do this in many ways, but i'll tell you about two.  first, in a terminal enter ```
sudo nautilus
```
second, press Alt+F2 and enter ```
gksudo nautilus
```

sudo and gksudo do the same thing, but sudo offers a terminal password prompt, and gksudo offers a graphical password box which appears on your screen.

once nautilus is opened as a super user, you can copy and move files in that window without restrictions.

---

### Post by jms1989 on 2006-08-08
Thank You! This is what I've been needing. :D:D

---

### Post by hopstah on 2006-08-08
you're welcome!

---

### Post by fuzzybabybunny on 2006-08-10
Thanks!

---

