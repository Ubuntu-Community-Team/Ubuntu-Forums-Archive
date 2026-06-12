---
title: "is apache &amp; php here"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by rcg40 on 2007-12-24
In synaptic package manager I see Apache2 2.2.3-4build installed and Apache2-common installed

I also see  libapache2-mod-php5 installed and php5, php5-cgi, and php5-cli installed.

When I try to load /var/www/phpinfo.html, Mozilla doesn't know how to open it.

What am I doing wrong?

Thanks and Happy Holidays.

---

### Post by ~LoKe on 2007-12-24
```
ls /var/www
```
Mind you, it should be phpinfo.php, not .html.

---

### Post by p_quarles on 2007-12-24
Also, when you're using your browser to open a file via the filesystem, you're completely bypassing Apache. To test the file, you'll need to point the browser to:
```
localhost/phpinfo.php
```

---

### Post by rcg40 on 2007-12-26
As a file 
 /home/richard/php_info.php is a file and when I click on it, it comes up in gedit.

now if I use mozilla and enter /localhost/php_info.php  I get 404 file not found

if I use /home/richard/php_info.php  in Mozilla's address line, Mozilla wants to know what to do with it.  If I say Yes to Open,  Mozilla downloads it.

Thanks in advance

---

### Post by LaRoza on 2007-12-26
[http://127.0.0.1](http://127.0.0.1)


Click it.

---

### Post by rcg40 on 2007-12-26
Thanks. Then I used Nautilus to build a folder  /var/www/myweb and things are ok

I should name it /var/www/htdocs

but that's for later on tonight.

---

