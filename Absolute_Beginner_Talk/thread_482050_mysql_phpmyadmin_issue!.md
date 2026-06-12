---
title: "mysql phpmyadmin issue!"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-06-23
i wanted to check out using mysql on amarok so i installed mysql, apache and phpmyadmin.

now when i go to: [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and try to log in with root i get:

> Error
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

what am i doing wrong?

---

### Post by ramzai on 2007-06-23
Is your MySQL server running?
Execute `ps aux | grep mysql`

---

### Post by Sushubh on 2007-06-23
[B] ps aux | grep mysql
sushubh   7623  0.0  0.0   2884   732 pts/0    R+   17:49   0:00 grep mysql
[/B]

---

### Post by ramzai on 2007-06-23
So your MySQL server is not running.
What package have you installed? There is no mysql package, you should have installed mysql-server.

---

### Post by Sushubh on 2007-06-24
alright doing that now... i tried installing mysql... whats that?

---

### Post by ramzai on 2007-06-24
I think it was just ignored as an invalid name. With mysql-server everything should work out of the box.

---

