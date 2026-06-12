---
title: "mysql functions don't work ?"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by MaaSTaaR on 2006-01-17
Hello ...

i am installed apache and php4 and mysql by these commands :

sudo apt-get install apache2
sudo apt-get install php4
sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install php4-mysql

apache and php now work fine , but the problem when i use mysql function with php script it's show for me it's now find mysql function

Fatal error: Call to undefined function: mysql_connect() in /var/www/test.php on line 3

the strange is i am installed phpmyadmin script and it's work fine !!

---

### Post by hen3rz on 2006-01-17
I think it might be because you havent installed the MySQL Server.
```
sudo apt-get install mysql-server
```

Below is what i did to set mine up:
```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```

---

### Post by iconmichael on 2007-07-24
> **hen3rz said:**
> I think it might be because you havent installed the MySQL Server.
```
sudo apt-get install mysql-server
```

Below is what i did to set mine up:
```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```

I installed as above up to the forth line.

when i tried 'sudo apt-get install php5-mysql' it gave me the following error;

"The following packages have unmet dependencies:
  php5-mysql: Depends: php5-common (= 5.2.1-0ubuntu1) but 5.2.1-0ubuntu1.4 is to be installed
E: Broken packages"

what does this mean and what do I do.

I tried installing php5-common and it says 'newest version already installed'.

---

### Post by LaRoza on 2007-07-24
Try using aptitude instead of apt-get, and installing MySQL first.

(if you wanted a LAMPP stack, "sudo tasksel" would have been easier, it will get everything all at once)

---

### Post by hyper_ch on 2007-07-24
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by iconmichael on 2007-07-24
I just did

sudo aptitude install php5-mysql

and it seems to have fixed some of the problems and finally installed php5-mysql

but I did phpinfo() and it still doesn't still make any refrences to mysql 

and I stil get the error :

Fatal error: Call to undefined function mysql_connect() in /var/www/php/testconnect.php on line 2 .

when attempting to connect to mysql via php

Thanks

---

### Post by LaRoza on 2007-07-24
Did you install MySQL?

sudo aptitude install mysql-server

---

### Post by Golyadkin on 2007-07-24
In the newer versions of PHP, the mysql functions are renamed to mysql**i**_connect() and so on.

---

### Post by LaRoza on 2007-07-24
The old functions still work, but if you are going to use the Improved functions, make sure you look them up, they are slightly different from the old ones.

---

