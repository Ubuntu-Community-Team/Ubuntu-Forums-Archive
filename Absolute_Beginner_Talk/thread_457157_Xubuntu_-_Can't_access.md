---
title: "Xubuntu - Can't access"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-28
Hi, I just installed Xubuntu Fiesty on an old pc of mine, and after I did some tweaking around with the system I suddenly discovered I couldn't access the "Users and Groups" application in the System menu.  When I try to open it up, after entering my password the following error message comes up:
[INDENT]Failed to run users-admin as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/INDENT]
Any Ideas about what to do?

---

### Post by taurus on 2007-05-28
Did you somehow remove yourself from groups adm and admin?

```
id
```

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

