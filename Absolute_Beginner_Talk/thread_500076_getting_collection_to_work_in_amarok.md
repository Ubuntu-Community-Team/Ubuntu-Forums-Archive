---
title: "getting collection to work in amarok"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by dascheer on 2007-07-13
when i try to update my collection on amarok in the "configure collection" panel i get the following error message:

"MySQL reported the following error:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
You can configure MySQL in the Collection section under Settings->Configure Amarok"

how do i need to configure MySQL?

---

### Post by Acglaphotis on 2007-07-13
Why dont you try sqlite? It works the same and no conf required

---

### Post by zanglang on 2007-07-13
First of all, do you have MySQL installed and running? It seems like you don't. If you're not sure what it is, or rather not muck around with installing a database server, you could just change your collection to use SQLite in Amarok's settings.

---

### Post by dascheer on 2007-07-13
yea that got my library to work!!

but now the problem is amarok wont display the directory i selected in the collections panel.  in fact, it's only displaying one artist from a directory i didnt select at all.

thanks a ton for the help

---

