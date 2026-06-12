---
title: "Mysql problem"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by macmurdo on 2007-12-03
I'm new to all this so I need help with getting mysql started.

I keep getting this message  - ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO

I'm getting desperate. What have I done wrong?

---

### Post by bwald on 2007-12-03
When you installed MySQL did you give it a root user password?  By default, the root MySQL user doesn't have a password, but from your error message it seems you do need one.  If you know the password try this:

```
mysql -u root -p
```

and then type the password at the prompt.

---

### Post by FakeOutdoorsman on 2007-12-03
You should take a look at the Ubuntu Wiki page on Apache, MySQL, and PHP, especially here: [Set mysql root password]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-b61e938a59a33a4e3a56552fa81a5ae0eec86651").

Other threads:
[MySQL Question]("http://ubuntuforums.org/showthread.php?t=105013")
[cant set the password with mysqladmin :(]("http://ubuntuforums.org/showthread.php?t=27156")

---

