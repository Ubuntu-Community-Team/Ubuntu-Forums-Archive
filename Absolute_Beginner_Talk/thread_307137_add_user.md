---
title: "add user"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by ivanperzan on 2006-11-26
Hi

trying to add user to ma home learning server 6.10 like this:
useradd -dhome/<username> -s/bin/bashrc -m <username>
user is created but when hi logs in his prompt doest say his curent dir or server name just $

checked for comments in skel and cannot see nothing why he will not dyplay is as <username>@<servername>:/home/<username>
can it be connected to groupes or something else?

please help

---

### Post by Rui Pais on 2006-11-26
hi, maybe trying with adduser:
```
sudo adduser <username>
```
will create user account and ask questions about any needed info or preferences for that user. 
It never failed to me.

---

### Post by xyz on 2006-11-26
Or:
System > Administration > Users and Groups > Add User...

---

