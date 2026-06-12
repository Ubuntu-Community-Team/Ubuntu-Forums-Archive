---
title: "please explain why apache path is different in linux than in widows"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by ofaolain on 2006-03-27
hi sorry to re post but its is doing my head in 
in linux i type [http://localhost/apache2-default/testphp.php](http://localhost/apache2-default/testphp.php)
but on windows i type [http://locahost/testphp.php](http://locahost/testphp.php)

is there a way that i can make it work on linux by only typing [http://locahost/testphp.php](http://locahost/testphp.php)


Cheers

Andy

---

### Post by RedKnight on 2006-03-27
locate your httpd.conf file mate should be in /etc/local/apache/conf/
Do a find on "apache2-default" you should then be able to see how to change the default dir.

If not post that section of your httpd here.

stuart.

---

### Post by Mr Green on 2006-03-28
Place testphp.php under /var/www instead of /var/www/apache2-default.

---

### Post by RedKnight on 2006-03-28
intresting, im yet to test apache on ubuntu but can you explain why theres 2 web directorys.....?

/apache2-default
and
/www

cheers

Stuart.

---

### Post by Mr Green on 2006-04-05
[QUOTE=RedKnight]intresting, im yet to test apache on ubuntu but can you explain why theres 2 web directorys.....?

/apache2-default
and
/www

cheers

Stuart.[/QUOTE]

apache2-default is just a default directory below www. Just delete it when you have other content there.

/var/www/apache2-default

---

