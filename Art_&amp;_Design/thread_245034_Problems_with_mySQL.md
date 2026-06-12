---
title: "Problems with mySQL"
date: 2006-08-27
forum: Art &amp; Design
---

### Post by dema on 2006-08-27
I'm installing mySQL like this:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_Database_Server](http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_Database_Server)

But when entering:
mysqladmin -h root@dennis-laptop -u root password my-password

I get this error:

mysqladmin: connect to server at 'root@dennis-laptop' failed
error: 'Unknown MySQL server host 'root@dennis-laptop' (1)'
Check that mysqld is running on root@dennis-laptop and that the port is 3306.
You can check this by doing 'telnet root@dennis-laptop 3306'


Can anybody tell me why?

---

### Post by Klaidas on 2006-08-27
Try using "localhost" instead of "root@dennis-laptop"

Again, this is a wrong subforum :)

---

### Post by dema on 2006-08-27
Now I enter:
mysqladmin -h localhost -u root password myPassword

And get this error:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

Why?

---

### Post by Klaidas on 2006-08-27
Hmm.
Try using [http://www.linux.org/lessons/interm/x2081.html#MYSQL-INTRO](http://www.linux.org/lessons/interm/x2081.html#MYSQL-INTRO)

---

