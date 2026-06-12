---
title: "Adduser without shell access"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by SmokeMasta on 2007-11-17
hi, i'm trying to setup a fileserver for the house and i need to be able to add users for samba but i dont want to give them shell access
 
so what is the way to adduser without shell access

---

### Post by x64Jimbo on 2007-11-17
Samba maintains its own list of users. You shouldn't need to block shell access to these accounts, because your system will not see them as system users. 
[http://www.comptechdoc.org/os/linux/manual4/sambausers.html](http://www.comptechdoc.org/os/linux/manual4/sambausers.html)
That should explain how Samba can be configured to use its own set of users, allowing you to skip that whole process.

---

