---
title: "Adding user with ssh"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by duckboy on 2006-03-29
I am trying to add a user to a computer remotely using ssh and need to know what commands I need to use to add the user

---

### Post by taurus on 2006-03-29
The command is adduser.

---

### Post by 5-HT on 2006-03-29
Appropriately enough, 'useradd' (or 'adduser').
You may also want to create a new group for the user with 'groupadd' (or 'addgroup').

For information, see:

man useradd
man groupadd

and/or

man adduser
man addgroup

HTH

---

