---
title: "lamp?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by jackss on 2006-04-05
hi, i want to build a web page using lamp, but im a noobie
can someone recommend me a good tutorial for installing,configurin and using it with examples and everything?
ill apreciate any help thanks

---

### Post by meborc on 2006-04-05
found this [http://www-128.ibm.com/developerworks/edu/wa-dw-wa-lamp-i.html](http://www-128.ibm.com/developerworks/edu/wa-dw-wa-lamp-i.html)

but you need to register :rolleyes:

---

### Post by adamkane on 2006-04-05
Here's LAMP for Ubuntu:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

I like to call it UAMP.

You can install the following with APT or Synaptic:
Apache1.3 or Apache2
PHP4 or PHP5
MySQL4 or MySQL4.1

If you want to install phpmyadmin with APT or Synaptic, then you have to install this particular configuration:
apache2 + php4 + mysql4 + phpmyadmin

It's possible to have the latest versions:
apache2 + php5 + mysql5 + phpmyadmin
but no one has written a HOWTO to use phpmyadmin with the latest version of PHP and MySQL. MySQL5 and phpmyadmin have to be installed from source.

Once you decide which versions you want to install, it is very difficult to uninstall and install a different version, so choose wisely.

---

