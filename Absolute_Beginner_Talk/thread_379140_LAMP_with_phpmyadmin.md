---
title: "LAMP with phpmyadmin"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by antigona on 2007-03-08
Hi all,

I have been trying for days to install php5, apache2, mysql and phpmyadmin to work together. After following some  tutorials and having followed the directions when i access [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) all i can is a list of difectories, no web interphase , nothing.

and if I try accessing localhost/testphp.php the browser asks me to download/oper the file instead of viewing it.

What could be wrong?

thanks in advance

---

### Post by WorldTripping on 2007-03-08
Hi,
 
Sound like you need to configure your httpd.conf file in Apache.
 
Looks like it's not processing the .php on the server before outputting it.
 
Here's some of the content of my httpd.conf

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

LoadFile "/www/php5/php5ts.dll"

LoadModule php5_module /www/php5/php5apache2.dll

Alias /phpMyAdmin "/www/phpMyAdmin"

<Directory "/www/phpMyAdmin">
	Options None
	AllowOverride None
	Order deny,allow
	Deny from all
	Allow from 127.0.0.1
</Directory>

<IfModule mod_mime.c>
	TypesConfig conf/mime.types
	AddType application/x-compress .Z
	AddType application/x-gzip .gz .tgz
	AddType application/x-rar-compressed .rar

	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php
		AddType application/x-httpd-php-source .phps
	</IfModule>
</IfModule>

<IfModule mod_dir.c>
	DirectoryIndex index.html index.php
</IfModule>

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Not sure that you'll need the first two lines as this was taken from a WAMP installation.

---

### Post by WorldTripping on 2007-03-08
Actually, 

I just found this:

[http://www.lamphowto.com/lamp.htm](http://www.lamphowto.com/lamp.htm)

And it says:

~~~~~~~~~~~~~~~~~~~~~~~~~~~

To ensure your PHP files are properly interpreted, and not just downloaded as text files, remove the # at the beginning of the lines which read:

#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps 
If the AddType lines above don't exist, manually enter them (without the leading # of course) after the line

AddType application/x-tar .tgz 

or anyplace within the <IfModule mod_mime.c> section of httpd.conf.

~~~~~~~~~~~~~~~~~~~~~~~~~~~

Also check that Apache is actually started.

---

### Post by antigona on 2007-03-08
:-)

Thank you, i'll give it a try!

---

### Post by antigona on 2007-03-08
well, I had a two hours break and restarted the process from scratch and it worked like a charm !

no idea what i did, but i followed this [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and voila !

i guess this time i actually took some time to read it throughfully.:rolleyes: :rolleyes: 

thanks for all the help!

---

