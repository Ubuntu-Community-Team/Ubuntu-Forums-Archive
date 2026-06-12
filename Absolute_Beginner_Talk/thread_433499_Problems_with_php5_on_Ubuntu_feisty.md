---
title: "Problems with php5 on Ubuntu feisty"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by cap_gemo on 2007-05-05
Hi everyone,

  I want to learn PHP now and in order to be able to write PHP-scripts and test them, i needed a php-installation. I istalled via apt the packages php5, apache2 and mysql-server. Then I created in my /var/www a test-PHP-script with ```
<?php phpinfo(); ?>
``` and tried to open it with a browser. I get the following message:



Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 80



  Unfortunately I couldn't find the error log file (if you could tell me, where it is, I'd post it here at once). I also tried running: ```

sudo a2enmod php5
/etc/init.d/apache2 force-reload      

```

Then I found in some guide, that one must add a line ```
AddType application/x-httpd-php .php
``` I did that too and restarted the apache server again. But all that didn't work. Can you help me, please?

---

### Post by RichGuk on 2007-05-05
The log should be at

/var/log/apache2/error.log


And as for the Internal Server Error, I've normally found that happens when you have some bad apache settings (I normally do it by naming something wrong in one of my .htaccess files).

```
tail /var/log/apache2/error.log
```

And let us know what it say :)

---

### Post by cap_gemo on 2007-05-05
Ok, here's the log:

```
[Sat May 05 12:09:10 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
PHP Warning:  Module 'json' already loaded in Unknown on line 0
[Sat May 05 12:09:13 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c mod_perl/2.0.2 Perl/v5.8.8 configured -- resuming normal operations
[Sat May 05 12:11:54 2007] [error] [client 127.0.0.1] SoftException in Application.cpp:297: UID of script "/var/www/testphp.php" is smaller than min_uid
[Sat May 05 12:11:54 2007] [error] [client 127.0.0.1] Premature end of script headers: testphp.php

```

I don't really understand much in PHP, but one think I understand: it doesn't like that PHP-script. But I saw this test-script on several websites with php-installing-guides. Is there anyway something wrong with the script?

P.S. Ok, I tested phpbb2, and it worked. Thanks anyway for your help!

P.P.S. Oh no, still having problems. I installed phpmyadmin to manage mysql-databases, but it won't run. Log:

```
[Sat May 05 12:27:39 2007] [error] [client 127.0.0.1] SoftException in Application.cpp:199: Script "/var/www/phpmyadmin/index.php" resolving to "/usr/share/phpmyadmin/index.php" not within configured docroot
[Sat May 05 12:27:39 2007] [error] [client 127.0.0.1] Premature end of script headers: index.php
[Sat May 05 12:28:01 2007] [error] [client 127.0.0.1] SoftException in Application.cpp:199: Script "/var/www/phpmyadmin/index.php" resolving to "/usr/share/phpmyadmin/index.php" not within configured docroot
[Sat May 05 12:28:01 2007] [error] [client 127.0.0.1] Premature end of script headers: index.php
```

I guess, something wrong is with php. Should I try it with php4?

---

### Post by jsaveker on 2007-07-31
I am having the very same problem... was this ever resolved.

I have only been using Kubuntu for a couple of days so I am not yet familar with file system permission and system rights and privialliages but I do think this is a permissions issue.

I have tried so many different things with no luck.....

If someone could suggest something then I would be most grateful.

---

### Post by sercra on 2007-10-11
I solve that problem adding to the vistual host config
into the directory tag:
AddHandler application/x-httpd-php .php

Since i use links I also add the Follow link option

---

