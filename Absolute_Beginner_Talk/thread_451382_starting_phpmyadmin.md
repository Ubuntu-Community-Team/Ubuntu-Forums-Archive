---
title: "starting phpmyadmin"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by jeff00z28 on 2007-05-22
I got it to install using sudo apt-get install phpmyadmin. But how do you start the gui?

---

### Post by Cypher on 2007-05-22
It's a PHP program, so depending on where it got installed, you would point your browser to it. So if your DocumentRoot is /var/www and if pointing your browser to [http://localhost](http://localhost) gets you that directory, and phpMyAdmin was a directory under there, you'd go to [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)..

---

### Post by jeff00z28 on 2007-05-22
thanks that worked! Have any idea what the default password for it would be?

---

### Post by Cypher on 2007-05-22
You should create a username/password combination in MySQL and then use that username to create any database you want. Take that username/password combo and put it into PhpMyAdmin's 'config.php.inc' file and you will have access to your databases..

---

### Post by jeff00z28 on 2007-05-22
/etc/phpmyadmin/ is where that file was located. I changed the username and password lines to the password I set w/ mysql but no luck. I deleted the "//" on those lines so they didnt look like comments. I used mysql –-user= bobob –password=bob from the command line.

---

### Post by jeff00z28 on 2007-05-22
any1 know? I can get into the software if I type root and no password about 4-5 times, but then I have to reenter it and startover again after a minute.  

I also changed the username and password lines in the /usr/share/phpmyadmin/config.inc.php and /usr/share/phpmyadmin/libraries/config.default.php

---

### Post by jeff00z28 on 2007-05-22
is there a line of code taht has to be changed to make it communicate w/ mysql?

---

### Post by az on 2007-05-22
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

