---
title: "new user"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-09
How to give sudo permissions to a new user please.


thanks

;) ;)

---

### Post by codejunkie on 2006-03-09
run
```
sudo adduser nameofuser admin
```
in a terminal.

---

### Post by Klejs on 2006-03-09
or

**sudo adduser name wheel**

would work I think, at least the user is given the opportunity to
use su wich gives the user root privileges.

---

### Post by Xian on 2006-03-09
The admin group is what appears in the sudoers file.
That is the trigger for users who should have sudo access.

---

