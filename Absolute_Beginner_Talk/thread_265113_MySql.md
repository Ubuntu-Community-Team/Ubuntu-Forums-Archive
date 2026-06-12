---
title: "MySql"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by toasted on 2006-09-25
I have the lamp server running but how do I work with MySql? I find no documentation that does me any good, at least not yet and ive been looking for hours. What is the default username and password? With the lamp install I assume there is a database installed... I installed MySql Admin but cannot log in without the info.

My goal is to get Mambo working. 
TIA

---

### Post by lamego on 2006-09-25
To find the mysql default user/pass :
[https://help.ubuntu.com/ubuntu/serverguide/C/databases.html](https://help.ubuntu.com/ubuntu/serverguide/C/databases.html)

MySQL documentation: [www.google.com](www.google.com), mysql documentation, 1st link:
[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by toasted on 2006-09-25
Well I didnt say that I found no info, just nothing I could use. The google link is a little lame  but thanks anyway.

---

### Post by lamego on 2006-09-25
> Well I didnt say that I found no info, just nothing I could use. The google link is a little lame but thanks anyway.
I don't know about your definition for lame, the mysql documentation site is the most complete documentation available for MySQL.

---

### Post by toasted on 2006-09-25
I had already been there and didnt find the passwords. Sometimes its very hard to find what one is looking for... I did look, and I meant the link to google itself. 

Using the Ubuntu link I tried what it said and this happened....

jack@bombertwo:~$ sudo mysqladmin -u root password ne wrootsqlpassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (us ing password: NO)'

---

### Post by transactionlogfiller on 2006-09-25
What happens if you just do

```
mysql -uroot
``` ?

---

### Post by toasted on 2006-09-25
> **transactionlogfiller said:**
> What happens if you just do

```
mysql -uroot
``` ?

jack@bombertwo:~$ mysql -uroot
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

also:
jack@bombertwo:~$ mysql -uroot -ppassword mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


jack@bombertwo:~$ mysql -uroot -p'' mysql
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

jack@bombertwo:~$ mysqladmin status
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'jack'@'localhost' (using password: NO)'


I have no idea what this all means, I am just following suggestions I found

---

### Post by toasted on 2006-09-25
Well, I uninstalled sqlserver and then reinstalled it. Same things happen.

---

### Post by dmizer on 2006-09-25
try this:
```
mysql -u root -p
```
if that fails, you have not added your root user correctly.

try this:
```
mysqladmin -u root -p password
sudo /etc/init.d/mysql restart
```
then try to log in as above.

if that doesn't work, i strongly suggest installing phpmyadmin.  it allows you a web interface to do all your nifty work in mysql.

---

### Post by toasted on 2006-09-26
> **dmizer said:**
> try this:
```
mysql -u root -p
```
if that fails, you have not added your root user correctly.

try this:
```
mysqladmin -u root -p password
sudo /etc/init.d/mysql restart
```
then try to log in as above.

if that doesn't work, i strongly suggest installing phpmyadmin.  it allows you a web interface to do all your nifty work in mysql.

jack@bombertwo:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


jack@bombertwo:~$ mysqladmin -u root -p password
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
jack@bombertwo:~$

jack@bombertwo:~$ sudo /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.


I had phpmyadmin installed but dont know how to start it. The phpmyadmin site is way too slow to use and locks up often. The info on that site does not jive with the files installed on my system either.. directories are different. When it says to    cd phpmyadmin  it does not work as there is no directory. All my phpmyadmin stuff is in /usr/share  as it was installed by Synaptic

---

