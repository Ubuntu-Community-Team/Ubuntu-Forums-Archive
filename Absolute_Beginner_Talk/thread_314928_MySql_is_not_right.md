---
title: "MySql is not right?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by prc320 on 2006-12-08
Hi

I have a problem, in this article the author said the following;

"So, let's start by installing *MySql*. Most distros split *MySql* into three packages: **mysql-server**, **mysql-client** and **libmysqlclient**" 

My problem is I added *MySql* Administration (**mysql-admin**) and *MySql* Query Browser (**mysql-query-browser**)

I have to start *MySql* by starting **/etc/init.d/mysql start**

But there nothing in **init.d** for *mysql*.

What do I do next?

Robert

---

### Post by compmodder26 on 2006-12-08
Are you sure that you installed mysql-server?  It should have placed a script in /etc/init.d.  It did it on my server.

---

### Post by prc320 on 2006-12-08
How do I do that?

---

### Post by Paul41 on 2006-12-08
> My problem is I added MySql Administration (mysql-admin) and MySql Query Browser (mysql-query-browser)

These are both GUI interfaces for MySql and not the MySql server

---

### Post by prc320 on 2006-12-08
> **Paul41 said:**
> These are both GUI interfaces for MySql and not the MySql server

What do I do, I want GUI version on MySql?

---

### Post by Paul41 on 2006-12-08
Once you install the server you can use these. You will connect them to "localhost". I am at a different computer right now so I can't get the name of the server package. Search in Synaptic for MySql and you should be able to find it. You want MySql 5. If you can't find it let me know and I will get the package name for you later today when I can get to my other computer.

---

### Post by compmodder26 on 2006-12-08
The package name is "mysql-server".

BTW, you can look up package names online too at:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by Paul41 on 2006-12-08
> BTW, you can look up package names online too at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Thanks for the link compmodder26. That will come in handy.

---

### Post by prc320 on 2006-12-09
Thanks very much................

You are superb.

Thanks!:D

---

