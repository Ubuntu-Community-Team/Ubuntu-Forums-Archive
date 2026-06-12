---
title: "I wanted to install mySQL..."
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-10-07
I have apache and php5 installed, I wanted to install mysql. I have all the repositories enabled but got no idea what to install. Anyone know what I should use? Also anyone know how to set the db's user's and pass's?
Thanks.

---

### Post by odinfromvalhalla on 2006-10-07
to install mysql:

```
sudo apt-get install mysql-server mysql-client
```

after you have it installied and running you can login to mysql typing mysql in a terminal then adding the following:
```
GRANT ALL PRIVILEGES ON test.* TO 'root'@'localhost' IDENTIFIED BY 'goodsecret';
```

more [info]("http://dev.mysql.com/doc/refman/5.0/en/grant.html")

---

### Post by Darrious on 2006-11-04
Because of me typing in this

```
GRANT ALL PRIVILEGES ON test.* TO 'root'@'localhost' IDENTIFIED BY 'goodsecret';
```I now can not start mysql. It says this

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

---

