---
title: "MySQL admin password"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-14
I'm following the instructions [here]("https://help.ubuntu.com/7.04/server/C/mysql.html").  I installed MySQL fine, but I'm having trouble setting the admin password.  When I do the command

sudo mysqladmin -u root password newrootsqlpassword

I get an error message:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I get the same error message with the next command.  What is the problem?

I'm running Ubuntu Server 7.04

---

### Post by FakeOutdoorsman on 2007-08-14
Try the commands listed on the Ubuntu Wiki ApacheMySQLPHP page:

[Set mysql root password]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-b61e938a59a33a4e3a56552fa81a5ae0eec86651")

---

