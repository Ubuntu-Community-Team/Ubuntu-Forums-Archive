---
title: "How do I fix this problem? I keep getting a warning when I run synaptic."
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by willy1234x1 on 2007-02-26
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I want to know how I could fix that it won't let me update anything or do anything.

---

### Post by Bachstelze on 2007-02-26
Have you tried running what it suggests ?

---

### Post by willy1234x1 on 2007-02-26
Yes it tells me I need to be a superuser.

---

### Post by aysiu on 2007-02-26
Try this, then: ```
sudo dpkg --configure -a
```

---

### Post by Maestro23 on 2007-02-26
> **willy1234x1 said:**
> Yes it tells me I need to be a superuser.

> sudo dpkg....

Read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

