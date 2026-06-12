---
title: "Partition problem"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by KriZo on 2007-06-09
Hey i got problems with a 132 gb ext3 partition, i cant use, cause i don't have the privileges to the disk, i can't write any thing to it. Can anybody help me?

---

### Post by alienexplorers on 2007-06-09
What type disk is it (USB, IDE, SATA)?

---

### Post by KriZo on 2007-06-09
Ide

---

### Post by alienexplorers on 2007-06-09
Go into terminal and enter:
> sudo chown username:username *.*
> sudo chmod 777 *.*

Not usre if I got these right.  Maybe someone will either share there knowledge or verify that this is correct.

---

### Post by KriZo on 2007-06-09
#4

Nope that didn't solved my problem :'(

---

### Post by KriZo on 2007-06-12
No one? I'm really missing, more disk space

---

