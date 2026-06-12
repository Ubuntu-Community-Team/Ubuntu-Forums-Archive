---
title: "PHP page shows the code"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by NoBullMan on 2005-12-13
Hi,
when I try to bring up a php page, it shows me the code instead of the page. I checked APache's config file and it has:

DirectoryIndex index.html index.htm index.shtml index.cgi index.pl index.php index.php3 index.xhtml

I tried [http://localhost](http://localhost) and it is showing me the contents of /var/www! I restarted Apache but no change.

Is there something else I should do?

---

### Post by aysiu on 2005-12-13
Can you post the output of these commands? ```
cd /var/www
ls
```

---

### Post by Swab on 2005-12-13
Have you installed php4-mysql ?

---

### Post by NoBullMan on 2005-12-13
root@WebServer:/var/www# ls
apache2-default  phpmyadmin  sharedip  webalizer

I checked the Synaptic and PHP-MySQL version 4.4.0-3 is installed.

---

### Post by Swab on 2005-12-13
Do you have these lines in your httpd.conf ?

```
AddType application/x-httpd-php .php 
AddType application/x-httpd-php-source .phps 
```

Apache needs to know what to do with php files...

edit: I have to go now.. hope someone can help you with this.

---

### Post by aysiu on 2005-12-13
[QUOTE=NoBullMan]root@WebServer:/var/www# ls
apache2-default  phpmyadmin  sharedip  webalizer[/QUOTE] So you don't have an index.html or index.php in your /www directory?

---

### Post by NoBullMan on 2005-12-13
I was following the document in howtoforge.com on how to set up a web server. During installation of Apapche it said to comment out the two lines you mentioned in the file /etc/apache2/mods-enabled/php4.conf.
I have uncommented them and now I can go to localhost/phpmyadmin. I created a test file with phpinfo() in it and it displays properly.

Shouldn't [http://localhost](http://localhost) display the apache screen (with the pink feather...)?

Thanks for your help.

---

