---
title: "Which php.ini to change?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-02-27
Hello,

I use ubuntu but this question is about the centOS server which I use at my webhost. Since this is my favourite forum I thought I would ask here..

I need to set allow_url_include to on. I SSH into the server and ran the command
find / -name php.ini

It returns the following:
find: /proc/29307: No such file or directory
/usr/lib/php.ini
/usr/local/lib/php.ini
/usr/local/Zend/etc/php.ini
/usr/local/cpanel/3rdparty/etc/php.ini
/scripts/php.ini

Which php.ini do I need to change? Why are there more than one actually?

---

### Post by kramer65 on 2008-02-27
Already found it! It was /usr/local/Zend/etc/php.ini

Thank you anyway!

---

