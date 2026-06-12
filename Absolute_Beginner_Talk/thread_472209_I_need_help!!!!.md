---
title: "I need help!!!!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by jdmasta on 2007-06-12
ok when i try to insert this "  _sudo gedit /etc/apt/sources.list_  "  into my ubnutu terminal to get ready to install beryl it pulls another termainal and say password so i try to type it and it dosent type anythin even other letters!!! WTF!!!   so if there is a way to diable the passwords or something I would be very greatful!!


P.S. im 13 and a noob i loved the beryl effects so i decided to ditch windows!

---

### Post by Clay_Banger on 2007-06-12
it is possible to remove the root password, but it is not recommended.

as for the no stars appearing when you type your password in, it is a security measure. what your are typing is still going there, its just you cant see it.

also for graphical applications you should be using gksudo instead of sudo

---

### Post by RedSquirrel on 2007-06-12
1. you should use gksudo with graphical applications.

```
gksudo gedit /etc/apt/sources.list
```

2. when you type in your password, it is going in, it just doesn't give any indication that it is. Don't worry. Just type in the password and press ENTER. :)

---

