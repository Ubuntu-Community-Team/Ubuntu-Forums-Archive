---
title: "gedit question (Solved)"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by NoBullMan on 2005-11-26
Hi,
I followed the steps in [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) to setup apache and PHP. When I open the file /etc/apache2/apache2.conf, it opens in "read-only" mode and won;t let me edit it.
Also, to test PHP, I created a test file using gedit but can't save it. I logged in using the user id and password I used during installtion.

---

### Post by NoBullMan on 2005-11-26
Hi,
I followed the steps in [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) to setup apache and PHP. When I open the file /etc/apache2/apache2.conf, it opens in "read-only" mode and won;t let me edit it.
Also, to test PHP, I created a test file using gedit but can't save it. I logged in using the user id and password I used during installtion. The document says to save it in /var/www/

---

### Post by invalid on 2005-11-26
This is less a question about gedit, and more a question about permissions.

To edit the configuration file, you need to have superuser permissions.
```
sudo gedit /etc/apache2/apache2.conf
```

By default, the /var/www directory is also owned by the root user, which means you will need to edit files there as a superuser as well (unless you chown it all)
```
sudo gedit /var/www/test.php
```

Then you can view it at:
[http://localhost/test.php](http://localhost/test.php)

Hope this helps,
Cb

---

### Post by aysiu on 2005-11-26
Your regular user has permission to edit only the files in /home/user
Every other directory (/etc and /var, for example) needs *root* or *sudo* privileges. Luckily, the first user you created during installation has sudo privileges. So just type ```
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf_backup
gedit /etc/apache2/apache2.conf
``` and you should be fine.

For more on permissions, read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

**Edit**: Gah! Beaten to it...

---

### Post by invalid on 2005-11-26
Someone must have combined these duplicate threads.. ignore this post.

Cb

---

### Post by aysiu on 2005-11-26
[QUOTE=invalid]Someone must have combined these duplicate threads.. ignore this post.

Cb[/QUOTE] I merged the two threads. Sorry!

---

### Post by NoBullMan on 2005-11-26
Thanks guys. I was missing the "sudo".
SOrry aout duplicate post. I thought I was editing the original post but apparently created a new one.

---

