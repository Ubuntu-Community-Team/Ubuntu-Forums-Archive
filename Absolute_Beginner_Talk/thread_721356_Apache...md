---
title: "Apache..?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by apocalypsxx on 2008-03-11
I have apache2 installed & php5..This is my 1st experience with them in Ubuntu or Linux for that matter..Have been using them succesfully on Windows..
There seems to be no htdocs folder & the httpd.conf is blank..I did try putting the phpinfo.php file in apache2 main directory but get this message..
----------------------------------------------------------------------------------------------
Not Found

The requested URL /apache2-default/phpinfo.php was not found on this server.
Apache/2.2.4 (Ubuntu) Server at localhost Port 80
---------------------------------------------------------------------------------------------
I get the feeling something is reallly wrong with my install..
-------------------
/etc/apache2/  
any help>tips much appreciated.
------------------

---

### Post by glennric on 2008-03-11
The default apache2 root is /var/www/apache2-default.  Try putting the file there.

---

### Post by hyper_ch on 2008-03-11
(1) config files are:

for apache2:  /etc/apache2
for php5: /etc/php5/apache2/php.ini (if php5 is loaded as module)

(2) default document root is /var/www/

---

### Post by Cypher on 2008-03-11
Be sure you've installed "libapache2-mod-php5" to get PHP working..

Also, I usually do the following to enable the public_html in your user directory so that you aren't using the "default" apache directory
```

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/userdir.load
sudo ln -s ../mods-available/userdir.conf
sudo /etc/init.d/apache2 restart

```
Now create the directory in your home directory
```

cd ~
mkdir public_html

```
Create all your files in the public_html directory and access it in the browser using http://localhost/~<username>.

---

### Post by hyper_ch on 2008-03-11
you don't need to symlink, use a2enmod

```

sudo a2enmod ...

```

```

sudo a2enmod userdir

```

```

sudo a2enmod php5

```

---

### Post by Cypher on 2008-03-12
That tool is useful, but at the end of the day it's symlink'ing as well..

---

