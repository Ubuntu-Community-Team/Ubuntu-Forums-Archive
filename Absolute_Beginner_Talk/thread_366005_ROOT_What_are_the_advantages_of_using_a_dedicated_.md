---
title: "ROOT: What are the advantages of using a dedicated administrator account?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by insyted on 2007-02-20
Ubuntu has one admin account: Root.
And it can have multiple user accounts.

Why not just have one account for administrator?
If it is a single user it shouldn't matter. They are the pc owner, and of course, have access to all the privilages.

If it is in a multiple user environment, the pc owner can be the administrator with all privilages, and set up user accounts for other users. Even for himself.

As it is currently, the pc owner is a user, and the rest of the users are users. This means that any user can log in, change root's password, enable root to log in, and do whatever they want as root.

What are the consequences for a single pc owner conducting normal computing as root?

---

### Post by Bachstelze on 2007-02-20
Wrong, not any user can use sudo. The file /etc/sudoers determines which users can use sudo and what they can do with it.

---

### Post by Resurrection on 2007-02-20
Have a look at this, I think it will explain Ubuntu Security better to you.  It is not quite the same as other Linux distros.

[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")

---

### Post by taurus on 2007-02-20
Maybe you want to read this also.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

