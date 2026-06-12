---
title: "Still cant get PHP to communicate with mysql"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by lekoya on 2006-07-24
can anyone advice me on step by step installation of appache, mysql and php.
Appache, mysql and php are all working fine. but i cant get php to communicate with php.

Thanx in advance

---

### Post by scxtt on 2006-07-24
i don't have a lot of experience getting it to work from scratch (it's already setup @ work, i just edit things) -- we use our own PHP files and have them work w/ myphpadmin MySQL databases ...

w/ that said, are you sure you're having your php code login to the database?, because once logged in, you should be able to query the database and use those values in PHP ...

---

### Post by risbac on 2006-07-24
Duplicate of [http://ubuntuforums.org/showthread.php?t=221818](http://ubuntuforums.org/showthread.php?t=221818)

---

### Post by lekoya on 2006-07-24
I get this the following error when i try to connect to DB.
"Fatal error: Call to undefined function mysql_pconnect()".

I think this can only mean one thing : there is no communication between php and mysql

Is there anything else i can do??

---

