---
title: "Users and Group applet fails to add user"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-02-21
I am trying to add a user to my system with the "Users and Group" applet in the Administration menu. I enter in all the information, username, Real name and password but when i push OK, nothing is added to the list of users. This error is strange because I was able to do this before but it no longer works.

---

### Post by y-lee on 2008-02-21
Strange. Did it ask you for your password and do you have superuser privilege?

---

### Post by y-lee on 2008-02-21
Wondering if you did it right :confused:

> Changes do not save

I've encountered this more often than you would imagine. It seems that people sometimes get confused when pressing the OK button during the steps above. You must not only press the OK button on the specific properties Window, but also press OK once again on the main Users and Groups window in order to save your changes.


See [Managing users in Ubuntu ]("http://www.reallylinux.com/docs/usersubuntu.shtml")

---

### Post by noorez on 2008-02-21
I did have superuser privileges when i started the application. It asked for my password.

---

### Post by y-lee on 2008-02-21
Does 

```
sudo adduser test
```
 

work?

EDIT: Where test is username :)

---

### Post by noorez on 2008-02-21
That works!

---

### Post by y-lee on 2008-02-21
I thought it would but it still leaves you with the GUI not working right :confused:

Confuses me But I've googled it and saw others with similar problems. To tired to deal with it now tho, maybe somebody will come along and know what to do. All I can do is guess and try a bunch of stuff I don't much about based on looking thru google results :lolflag:

Anyway I'll check back in day or two.

good luck!

---

