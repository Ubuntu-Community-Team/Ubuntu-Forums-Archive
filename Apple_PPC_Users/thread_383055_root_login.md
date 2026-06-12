---
title: "root login"
date: 2007-03-12
forum: Apple PPC Users
---

### Post by macminiuser on 2007-03-12
How do  a person login as root with Ubuntu 6.06?

---

### Post by Tipo on 2007-03-12
usually, you would login with username 'root' and your password.

There are many ways to be root without really being root, though.  The sudo (superuser do) command will give you admin privileges to edit files that you wouldn't be able to edit before.

And if you want an actual root shell, open Terminal and type:

```
sudo su
```

Enter your password, and you have a root shell :)

Be careful in there though... the system will do what you tell it. Including nuking itself :P

---

### Post by ssam on 2007-03-14
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) is a big article on root and sudo on ubuntu.

---

