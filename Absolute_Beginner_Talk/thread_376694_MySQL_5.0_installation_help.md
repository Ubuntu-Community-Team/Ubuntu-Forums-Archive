---
title: "MySQL 5.0 installation help"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by b00mer on 2007-03-05
OK. I'll admit it. I'm a dumb-*** that has truely screwed up the MySQL install and can't fix it.

I had MySQL 5 installed on Ubuntu 6.06 Desktop. After intial installation, I could run MySQL Administrator and connect to the server fine, just couldn't do any admin work. At this point, I had NOT tried to edit the config files at all. Once I modified the config file etc/mysql/my.cnf to add the root password, abosulutely NOTHING worked! I tried removing the application through Synaptic Package Manager including all the configuration files, then reinstalled it, but to no avail. I think I may have screwed up the root password somehow in a file that wasn't removed.

When I try to run MySQL now, I get:
Could not connect to host 'bvc-server'.
MySQL Error Nr. 1045
Access denied for user 'root'@'localhost' (using password: NO)

or 

Could not connect to host 'bvc-server'.
MySQL Error Nr. 1045
Access denied for user 'root'@'localhost' (using password: YES)

if I try using what I think the password was. How do I work my way out of this mess and configure MySQL right? I've looked at directions on how to reset the root pasword, but have problems making that work too.

---

### Post by jvc26 on 2007-03-05
Hmm I've never changed the root password by altering the config file in MySQL, rather from a line from the terminal...
As a possibility - execute:
```

sudo apt-get --purge remove mysql-server mysql-query-browser mysql-admin

```
Then go to your user directory, show hidden files and check that there is no .MySQL file - if there is, delete it.
Then, try:
```

sudo apt-get install mysql-server mysql-query-browser mysql-admin

```
And once installed:
```

mysqladmin -u root password your-new-password
sudo /etc/init.d/mysql restart

```
Then to log in to mysql prompt:
```

mysql -u root -p

```
and it will then ask you for the password.
I hope that works!
Il

---

