---
title: "List all registered users"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-08-26
Gday, 

I have installed a number of programs/utilities that have created users on my 7.04 server install.

How can i list all the users registered on my system? (not just the ones logged in)

cheers

c.

---

### Post by finer recliner on 2007-08-26
cat /etc/passwd


you want to research how to read the passwd file. theres lots of information stored there.

---

### Post by Majorix on 2007-08-26
Does
```
users
```
work?

---

### Post by finer recliner on 2007-08-26
> **Majorix said:**
> Does
```
users
```
work?

sorry, wrong.

man users says that this only displays who is currently logged in. he wants to know what ALL the user accounts are.

---

