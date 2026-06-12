---
title: "[SOLVED] only allow root to change user passwords"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-01-20
Hey all,

I want the only way for a password to change on my system is if root performs the change. 

how can i make this happen

thanks, 
kt

---

### Post by bwtranch on 2008-01-20
That's the only way.

---

### Post by jordanmthomas on 2008-01-20
> **bwtranch said:**
> That's the only way.

No, a user can change his own password.

One way to do accomplish what you want is to make it so that only root can execute the program passwd.
chown it to be root's (should already be probably) and then chmod it to 700 should work.

Any user that can use sudo could still change his password though.

---

### Post by kernel tom on 2008-01-20
> **jordanmthomas said:**
> No, a user can change his own password.

exactly, and I don't want to let any user change their own password

---

### Post by jordanmthomas on 2008-01-20
I've added more to my post now, in case you didn't see it.

---

### Post by kernel tom on 2008-01-20
ah thanks, duh that makes so much sense

---

### Post by jordanmthomas on 2008-01-20
You should be able to stop sudoers from doing it too if you want to edit your /etc/sudoers file
```
sudo visudo
```

It should be documented in there how to do it.

---

