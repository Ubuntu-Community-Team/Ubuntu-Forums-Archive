---
title: "sudoers file"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by xstation on 2008-04-10
please remind me how to add /ubuntu/andy to sudoers file 
so i can run ubuntu/andy: sudo apt-get etc etc


thanks

xstation

---

### Post by clarknova on 2008-04-10
I don't think you need to mess with the sudoers file since about 6.06 or thereabouts. If you add the user (or change into) as an administrator then that user should be able to sudo.

db

---

### Post by tamoneya on 2008-04-10
in ubuntu you add the user to the admin group.```
usermod -G admin andy
```.  This will either have to be done with su or be done with a different user so that it can be called with sudo.

---

### Post by aysiu on 2008-04-10
This should help you out:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

