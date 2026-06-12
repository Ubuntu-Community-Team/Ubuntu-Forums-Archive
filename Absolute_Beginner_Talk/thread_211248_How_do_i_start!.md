---
title: "How do i start!"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-07-08
Hey all!

I have this proble.

I think that i have installed PHp MySQL and Apache + PHPmyAdmin,

How do i get all these things satarted and see all are installed correctly.

PLease lead me the rightr way!

---

### Post by verbatim210 on 2006-07-08
[http://localhost/](http://localhost/)

if you can see phpmyadmin then it works.  ALL of it.

---

### Post by hardfire_avk on 2006-07-08
Hey!

[http://localhost](http://localhost) didn't work

but when i exit ubuntu it says.

Stopping Apache 2 webserver and stopping mysqserver (mysqld) Which means they are installed.

What is the prblem.

Thanks for helping

---

### Post by DSn0wMan on 2006-07-08
> **hardfire_avk said:**
> 
Stopping Apache 2 webserver and stopping mysqserver (mysqld)

That only means that apache and mysql are running. I an not an expert, but I would double check my apache config.

---

### Post by hardfire_avk on 2006-07-09
> **DSn0wMan said:**
> That only means that apache and mysql are running. I an not an expert, but I would double check my apache config.

How do i check my apache configuration.??

---

### Post by hardfire_avk on 2006-07-09
And what bout PHP. how do i see it has been installed correctly or not.

And what bout the Apache Configuration. how do i see it?

---

### Post by DSn0wMan on 2006-07-09
To view your apache2 configuration: ```
gedit /etc/apache2/apache2.conf
```

You might take a look at the apache2 wiki, if you haven't allready.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I think this acurately describes the steps required to get Apache and MySQLPHP working.

You also may want to ask questions of this nature in the server forum rather than beginner talk.

---

### Post by tribaal on 2006-07-09
Usually I pont my browser at [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to finish setting up mySQL.

Then I do a test php page I put in /var/www that contains only the following lines:

```
<?php
phpinfo();
?>
```

point your browser to it. If you see the php info page then it works, otherwise it means your php setup is missing something.

Cheers

- trib'

---

### Post by verbatim210 on 2006-07-10
sudo /etc/init.d/apache2 restart
restarts apache2

[http://127.0.0.1/](http://127.0.0.1/)
as soon as you install apache,
/var/www contents are hosted
at that above address.

if this doesn't work let us know what happens.

also please show the output of...
netstat -plantu

---

