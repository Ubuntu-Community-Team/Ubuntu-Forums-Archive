---
title: "MySQL Problem"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by apachesoul on 2005-08-09
apachesoul@apachebase:~$ mysqladmin -u root password db_user_password
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
apachesoul@apachebase:~$ mysqladmin -u root password db_user_password
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
apachesoul@apachebase:~$

I just wanted to setup mysql. I followed instructions about setting up mysql server in forum bhut I couldn't get success. I first installed 4.1 (No success) tried 4.0 (downgraded) but now this errors occured.

And a big problem there are lots of checked repositories in synaptic package manager. I'm so confused about this and I want to start from begin. But I dont want to install ubuntu again. What must I do? Plz help I'm going to be mad.... ](*,)

---

### Post by ltmon on 2005-08-09
Doe this help?

[http://www.tech-recipes.com/mysql_tips762.html](http://www.tech-recipes.com/mysql_tips762.html)

L.

---

### Post by apachesoul on 2005-08-09
[QUOTE=ltmon]Doe this help?

[http://www.tech-recipes.com/mysql_tips762.html](http://www.tech-recipes.com/mysql_tips762.html)

L.[/QUOTE]
 thanks pal but didn't work :(

---

### Post by ltmon on 2005-08-09
Hmmmm....

Ok:

1. Check the permissions of the sock file

2. Type:

> ps aux | grep mysqld

to make sure the daemon is running properly.

These are the only other reasons that I know that could be causing this.

L.

---

### Post by apachesoul on 2005-08-09
[QUOTE=ltmon]Hmmmm....

Ok:

1. Check the permissions of the sock file

2. Type:

> ps aux | grep mysqld

to make sure the daemon is running properly.

These are the only other reasons that I know that could be causing this.

L.[/QUOTE]
 apachesoul@apachebase:~$ ps aux | grep mysqld
1000     13612  0.0  0.1   2908   604 pts/0    R+   03:41   0:00 grep mysqld

whats thats mean?

---

### Post by ltmon on 2005-08-09
[QUOTE=apachesoul]apachesoul@apachebase:~$ ps aux | grep mysqld
1000     13612  0.0  0.1   2908   604 pts/0    R+   03:41   0:00 grep mysqld

whats thats mean?[/QUOTE]

That means mysql isn't running.  I gather you probably followed ubuntuguide.org to install mysql, but it seems that you need to manually start the server.

To start the server (I think):

> sudo /etc/init.d/mysql start

You might want to use boot up manager to cause this to start on login every time.

L.

---

