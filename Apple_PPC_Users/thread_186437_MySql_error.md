---
title: "MySql error"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by Brandenwill on 2006-06-01
I have just got done installing Ubuntu for the first time. Anyway I was trying to setup a lamp server. I followed this guide [http://www.linuxforums.org/servers/setting_up_a_server.html](http://www.linuxforums.org/servers/setting_up_a_server.html) but when I try to use PHP to connec to Mysql I get this error: Fatal error: Call to undefined function mysql_connect() in /var/www/data.php on line 10. What could cause this error? I will say that I am a serious newbie to the linux game so go easy on me if the answer is complex. Any help would be awesome.

---

### Post by felinux on 2006-08-31
Try checking the procedure outlined here:

[http://www.experts-exchange.com/Web/Web_Languages/PHP/PHP_Databases/Q_20345181.html](http://www.experts-exchange.com/Web/Web_Languages/PHP/PHP_Databases/Q_20345181.html)

---

### Post by jpowermacg5 on 2006-09-01
What u need to do is edit the /etc/php.ini file, and uncomment the mysql line... then restart apache and it should work.

---

