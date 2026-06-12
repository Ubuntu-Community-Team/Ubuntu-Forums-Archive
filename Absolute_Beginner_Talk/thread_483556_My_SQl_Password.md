---
title: "My SQl Password"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Earltnm on 2007-06-24
Hi,  trying to setup My SQL password. It's asking for a password first time in and I don't know what the password is:

iman@iman-desktop:~$ sudo mysqladmin -p -u root -h localhost password newrootsqlpassword
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Any ideas?

Thanks,  Rick

---

### Post by ajmorris on 2007-06-24
> **Earltnm said:**
> Hi,  trying to setup My SQL password. It's asking for a password first time in and I don't know what the password is:

iman@iman-desktop:~$ sudo mysqladmin -p -u root -h localhost password newrootsqlpassword
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Any ideas?

Thanks,  Rick

is mysqld running?

---

