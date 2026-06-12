---
title: "Network DataBase"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by FKi on 2007-10-16
I need to figure out how to make a database on a server, then be able to access and edit decently small files, its for a business setting.   any suggestions?

---

### Post by Old *ix Geek on 2007-10-17
When you say that you "*need to figure out how to make a database on a server*," do you mean you're going to write a database program yourself, or you're going to use an existing commercial database package, on a server?

If the former...you're in for quite a lot of work!  Writing a database program is no small task.

If the latter, you just need to place the database's program(s) on the server and/or individual workstations, according to its documentation.  Of course you'll have to be sure the database you choose is a network version, supports multiple simultaneous users, provides record locking (so two people can't modify the same record at the same time), is in a location that's accessible by the appropriate users, etc.

You'll get better/more helpful answers if you clarify what you're referring to. :)

---

