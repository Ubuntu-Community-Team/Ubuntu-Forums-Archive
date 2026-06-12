---
title: "username/password"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by zzzPOOHzzz on 2007-04-05
is there a default logon or something? because i installed ubuntu... and it wont let anything as a username... any of my typical usernames... or like admin or root or anything like that....

---

### Post by h0ax on 2007-04-05
You didn't set up a user during the install process?
Have you tried no username just entering?

---

### Post by taurus on 2007-04-05
Did you use the desktop CD or the alternate CD?  Try using **oem** as your login name and the same password that you've created during the installing process.  Then, run this command from a prompt to create an actual account for you to use from now on.

```
sudo oem-config-prepare
```

---

### Post by zzzPOOHzzz on 2007-04-05
awesome... oem worked... thanks a ton... i'm sure i'll be back on here for more questions haha


thanks again

---

