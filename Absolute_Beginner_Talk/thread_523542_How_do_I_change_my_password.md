---
title: "How do I change my password?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by rob7391 on 2007-08-12
Having installed Ubuntu as a newbie a while back and grown to love it I find that I would now like to change my password to make it somewhat more secure. How do I do that? I am of course the root user and so it is the all important password.
:(

---

### Post by undertakingyou on 2007-08-12
Assuming that you are using gnome, if you go to System => Administrator => Users and Groups you can change it there.

---

### Post by aysiu on 2007-08-12
You are not the root user "of course." The root user cannot be logged into by default in Ubuntu.

You are an admin user who is usually a limited user and can temporarily assume root privileges for individual tasks after a password authentication.

undertakingyou's advice is good.

If you prefer the terminal, type ```
sudo passwd rob
```

---

### Post by Bachstelze on 2007-08-12
> **aysiu said:**
> 
If you prefer the terminal, type ```
sudo passwd rob
```

Tip : to avoid users typing *sudo passwd rob* litterally, tell them to type *sudo passwd $(whoami)*, which will work whatever their username is ;)

EDIT : but for the current user, just typing *passwd* is enough.

---

### Post by aysiu on 2007-08-12
Thanks for the clarification, HymnToLife.

---

