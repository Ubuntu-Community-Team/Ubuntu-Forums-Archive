---
title: "Torrentflux"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Giorgis on 2007-03-11
I am having problems with torrentflux

I installed 2.3 and then 2.2 with the same problem. 

Once I follow all the steps, and I go to the appropriate web address I get the following in one line.

Fatal error: Call to undefined function: mysql_connect() in /var/www/tf/adodb/drivers/adodb-mysql.inc.php on line 354

I get the same error message with both torrent flux 2.2 and 2.3 

Heeeelp

G

---

### Post by tribble222 on 2007-03-11
I typed your error message into google and found this in the TorrentFlux FAQ

"Fatal error: Call to undefined function: mysql_connect() in /var/www/html/adodb/drivers/adodb-mysql.inc.php on line 354
This means that your version of php can't connect to the mysql database. Usually installing a package like php-mysql will solve this although if it doesn't then open your php.ini file and find the line like extension=mysql.so, remove the comment from in front, and then restart your webserver."

Hope that helps!

---

### Post by Giorgis on 2007-03-12
Thanks for the reply, and also for the technique in solving problems. I will try it soon

G

---

