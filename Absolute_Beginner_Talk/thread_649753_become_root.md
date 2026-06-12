---
title: "become root"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by psergiu on 2007-12-25
i can't sign in as root!!

i execute su and then it asks me for the root password which i never set(when i installed it i was asked to supply a username and a password which with limited priviliges)

what's wrong?

---

### Post by TidusBlade on 2007-12-25
Go to the account or user management and look around in the system accounts, and you should find root and set the password for it.

---

### Post by taurus on 2007-12-25
Try using sudo instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by LaRoza on 2007-12-25
@OP The root account is not enabled, you can run selective programs as root with sudo and gksudo.

---

### Post by zvacet on 2007-12-25
To become root

```
sudo -i
```

and type your password

---

### Post by runris on 2007-12-25
how can you sign in as root in GUI? any way?

---

### Post by taurus on 2007-12-25
> **runris said:**
> how can you sign in as root in GUI? any way?

What do you need to run?  Try

```
gksudo **GUI_app**
```

---

