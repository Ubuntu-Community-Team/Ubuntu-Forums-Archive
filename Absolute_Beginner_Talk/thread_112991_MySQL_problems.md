---
title: "MySQL problems"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Newbify2 on 2006-01-05
I've searched through this forum and tried everything, nothing seems to work, any help would be greatly appreciated. I guess this wouldn't really be absolute beginnner because I've been using ubuntu for awhile but I'm an absolute beginner with MySQL on Ubuntu.


I've done:

sudo apt-get install mysql-server

when I try:
```
mysqladmin -u root password 'password'
```
or
```
mysqladmin -u root password -p
```

I get:

```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: YES)'

```

My /etc/hosts file looks like this
```
127.0.0.1       localhost       localhost.localdomain   winston
```

And of course:
```
mysql -u root -p
```
only returns:
```
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)
```

Any ideas? [edit] btw I'm using Breezy... [/edit]

---

### Post by Zelut on 2006-01-05
I've always had problems using mysql from the terminal.  Have you tried installing phpmyadmin & going that route?  I always have a much easier time doing that..
sudo apt-get install phpmyadmin

see if you can get things configured from there..

---

### Post by papayiya on 2006-01-12
Ok...

If you do 

```
mysqladmin -u root password 'password'
```

you set the password for mysql

now.. login to mysql:

```
mysql -u root password -p
```

type in your password... i.e. password

Good luck,
George

---

