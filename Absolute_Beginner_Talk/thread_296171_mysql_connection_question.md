---
title: "mysql connection question"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by uraliss on 2006-11-09
Hi Folks,
I have just started messing around with mysql on my server and it seems to be working fine.

What I wish to do now though is connect to the database from a remote computer using the mysql client. I have fumbled around for a bit but haven't managed to get this working yet.

Can someone tell me what I need to do to get this working.

My database is on ip 192.168.0.100 and the database is called tasklist

Many thanks in advance.

---

### Post by davmac on 2006-11-09
To get this working I had to set up a new user and grant it the relevant rights. On the box where mysql is installed, start mysql and type "GRANT ALL ON * TO [email]userid@XXX.XXX.XXX.XXX[/email] IDENTIFIED BY "password";

Where XXX.XXX.XXX.XXX is the ip address of the connecting machine.

You should then be able to connect from the remote machine with this userid and password.

BTW: If you don't want the remote user to be able to do anything to everything, have a look at the syntax of GRANT to allow more restrictive access.

Hope this helps,

Dave Mac

---

### Post by otherdave on 2006-11-09
One other thing to check: the mysql config file in /etc/mysql/my.cnf (I think).

[This post](http://www.debianadmin.com/mysql-database-server-installation-and-configuration-in-ubuntu.html) has more detail on the matter, but mysql comes pre-configured to not allow connections from other computers (for security reasons). It's easy to turn this on, but if you're having problems connecting from another machine, this could be why.

---

### Post by uraliss on 2006-11-09
hi and thanks for the help so far.

I have edited my /etc/mysql/my.cnf file and that seems ok

the only thing im struggling with now is ...

what is the syntax of the mysql command to get it to point at my server?

I can't seem to find this info anywhere. lol

---

### Post by otherdave on 2006-11-09
You can do 'man mysql' from a terminal to view the help pages for the mysql command :)

--host is probably what you're looking for. I'd guess something like:

mysql --host 111.222.333.444 --user=myuser --password=mypassword my_database_name

Of course, you'll switch the IP address, username, password and database name to whatever you've set up.

---

