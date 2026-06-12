---
title: "phpMyAdmin help"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by cinmachina on 2007-05-20
Hello all.

I have installed a LAMP server using the following instruction guide for feisty fawn 7.04:
[http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/page-7.htm](http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/page-7.htm)

Everything seemed to install fine, but when I go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/), it is asking for a username and password. 

Bare in mind this is the first time I've used anything like this, and I'm totally noob. 

How do I set a username and password in this to get it to work? I've use admin/admin, administrator/administrator, nothing logs me in.

Is there a config file somewhere I can edit or something?

The error message I get is as follows:

#1045 -- Access denied for user 'administrator@localhost' (using password: NO)


Can anyone help me get this working?

Laymens terms preferred please!

---

### Post by Ozeuss on 2007-05-20
phpmyadmin uses the same user that mysql uses. so if you set up a user for mysql, use that.
if you haven't:
Set mysql root password

Before accessing the database by console you need to type:

```
mysql -u root
```

At the mysql console type:

```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
```

A successful mysql command will show:

```
Query OK, 0 rows affected (0.00 sec)
```

Mysql commands can span several lines. Do not forget to end your mysql command with a semicolon.

Note: If you have already set a password for the mysql root, you will need to use:

```
mysql -u root -p
```

this is extracted from- [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by cinmachina on 2007-05-20
Worked like a charm, you're the man!

---

### Post by cinmachina on 2007-05-20
Ooops! Spoke too soon ;(

How do I view the files I've placed in my public_html folder from another computer?

I thought it would be in http://<my ip>

I hope I'm explaining this ok.

---

### Post by Ozeuss on 2007-05-20
other computer users might not have read permissions to your file, so check that.
it also might be a firewall issue (iptables?)
i haven't tried making my local apache accesible from the outside (quite the contrary, actually)...

---

