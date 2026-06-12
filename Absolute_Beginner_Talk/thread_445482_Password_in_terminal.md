---
title: "Password in terminal"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by JMV290 on 2007-05-16
When I try to do something in the terminal and it asks me for my password it doesn't work.  I cant type anything for a password.


It is really annoying.  Without it I cannot install flashplayer, and many other things.
What do I do?


edit: Okay, I was able to use the automatic installation for flashplayer but the password issue still stands.

---

### Post by Gmbrdilos on 2007-05-16
it seems like it is not typing but it actually IS
so just type your password and hit enter

---

### Post by JMV290 on 2007-05-16
> **Gmbrdilos said:**
> it seems like it is not typing but it actually IS
so just type your password and hit enter

Really?  Alright, I'll remember that.



Also, how do I do this?   I know how to edit it and add the line but I cannot save it.

1. Edit /etc/apt/sources.list and put this line:

    deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main


I'm trying to install a theme.

---

### Post by Gmbrdilos on 2007-05-16
hit alt+F2
type: gksudo nautilus
in that window go to whatever file you want to edit, find and edit it.

---

### Post by aysiu on 2007-05-16
Read these two links:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by BHelts on 2007-05-16
you can also try 
```
gksudo gedit /etc/apt/sources.list
```
which will then give you a button to save.

---

