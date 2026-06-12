---
title: "phpmyadmin installation infor for 7.04?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by boardtc on 2007-05-28
I want to install phpmyadmin so I can restore some sql databases to my new 7.04 desktop system.  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) talks about first enabling the universe repository but the link it refers to [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) has information for an older version of ubuntu. Software Preferences do not exist and are now software sources and I cannot find the add channel option it mentions. Is there more update documentation available?

Thanks, Tom.

---

### Post by energiya on 2007-05-29
To install phpmyadmin you must have installed on your PC mysql, php and a webserver. You would be better with [XAMPP]("http://www.apachefriends.org/en/xampp-linux.html"). It's very easy to install and does not require hardcore tweaking.
> 
XAMPP is an easy to install Apache distribution containing MySQL, PHP and Perl. XAMPP is really very easy to install and to use - just download, extract and start.


It installs phpmyadmin too :)

---

### Post by boardtc on 2007-05-29
Thanks for the reply but I already have lamp installed and cannot go through that again. I ended up skipping that step and just doing the install. What's that step for? Seems like it'd redundant. Can it be removed from the instructions or marked as optional so other people don't waste their time like me.

---

### Post by energiya on 2007-05-30
> **boardtc said:**
>  I ended up skipping that step and just doing the install. What's that step for? Seems like it'd redundant. Can it be removed from the instructions or marked as optional so other people don't waste their time like me.

I don't fully understand you... 
> **http://www.phpmyadmin.net/documentation/#require]
**PhpMyAdmin requirements**
    * PHP
          o You need PHP 4.1.0 or newer, with session support (see FAQ 1.31)
          o You need GD2 support in PHP to display inline thumbnails of JPEGs ("image/jpeg: inline") with their original aspect ratio
          o You need PHP 4.3.0 or newer to use the "text/plain: external" MIME-based transformation
          o When using the "cookie" authentication method, the mcrypt extension is strongly suggested for most users and is required for 64–bit machines. Not using mcrypt will cause phpMyAdmin to load pages significantly slower.
    * MySQL 3.23.32 or newer (details) said:**
> 

If you have lampp installed. just start it
```

sudo /opt/lampp/lampp start

```
(if you have it installed in /opt/lampp)

You should see in the terminal something like
[quote]
Starting XAMPP for Linux 1.6...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.


...and then write (if starting the server works)
```

firefox http://localhost/phpmyadmin

```

I hope I understand what you are trying to do...

---

### Post by boardtc on 2007-06-23
Please can I go back to my original question, I just want to install PhpMyAdmin. I do not have lampp installed. can anyone provide instructions for 7.04, thanks?

---

