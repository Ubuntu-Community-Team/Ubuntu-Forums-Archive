---
title: "PHPMyAdmin"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by mattywarr on 2008-04-21
Me again!

I'm trying to configure phpMyAdmin - I've installed it and LAMP through apt-get and all seemed to be OK. But when i browse to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) (Which is where its meant to be) nothing appears.

Have I missed a step somewhere?

Matt

---

### Post by Squizz on 2008-04-21
What happens when you go to [http://localhost/](http://localhost/) ?  Does it say "congratulations, apache is working" or something similar?

If it doesn't, then you need to make sure your server is complete (including installing PHP).

If it does, then are you sure you extracted the files, and not just download the archive?  If so, then follow the instructions at [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin) .

---

### Post by mattywarr on 2008-04-21
> **Squizz said:**
> What happens when you go to [http://localhost/](http://localhost/) ?  Does it say "congratulations, apache is working" or something similar?

If it doesn't, then you need to make sure your server is complete (including installing PHP).

If it does, then are you sure you extracted the files, and not just download the archive?  If so, then follow the instructions at [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin) .

[http://localhost](http://localhost) takes me here

> Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 20:16 	-
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 Server at localhost Port 80

And clicking the apaches-default folder takes me to say "It works!"

I installed phpmyadmin using the apt-get method described in the link you sent, and I have rebooted my PC and the apache server too but still no luck :(

---

### Post by Squizz on 2008-04-21
What's the error when you go to [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php) ?  Does it look like it's installed but has errors or not installed at all?

Have you tested php?  To do that, make a new file called test.php on your server.  Put the following in the file:

[php]
<? phpinfo(); ?>
[/php]

That should show you a whole bunch of information if it's set up properly.

Failing that, uninstall it completely using synaptic, and try reinstalling?

Other than that I wouldn't know what else to try sorry.

---

### Post by mattywarr on 2008-04-21
php info gives me this.

> PHP Version 5.2.3-1ubuntu6.3

System 	Linux matt-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date 	Jan 10 2008 09:24:13
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini
PHP API 	20041225
PHP Extension 	20060613
Zend Extension 	220060519
Debug Build 	no
Thread Safety 	disabled
Zend Memory Manager 	enabled
IPv6 Support 	enabled
Registered PHP Streams 	zip, php, file, data, http, ftp, compress.bzip2, compress.zlib, https, ftps
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters 	string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, convert.iconv.*, bzip2.*, zlib.*

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

The folder phpmyinfo isn;t even there...

---

### Post by crs0328 on 2008-04-21
I actually had this same problem last week.  Here is what I did to fix it.  

The problem was that when I installed phpmyadmin, it didn't create a symbolic link from apache to phpmyadmin.

With my apache document root being /var/www  , I typed this into terminal:

```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

"ln" - meaning "make link" | "-s" - meaning "symbolic link"

Hopefully that works for you!

---

