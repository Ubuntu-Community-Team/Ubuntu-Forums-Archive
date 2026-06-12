---
title: "Help. php setcookie() not working"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by insub2 on 2007-05-20
I'm learning php and have turned my laptop into a LAMP server.

I was following a online tutorial and ran into a problem.

if i try and set the cookie anyplace but the very beginning of the file, i get
```
Warning: Cannot modify header information - headers already sent by (output started at /var/www/test/test.php:11) in /var/www/test/test.php on line 15
This is visit number 0
```

i've tried messing with the /etc/php5/apache2/php.ini file, turning output_buffering to On.

Thanks in advanced

---

### Post by bobplano on 2007-05-20
they need to be at the begginning of the file, im geussing because you are using headers. its just an warning so you don't really have to worry about that, but headers go before any output, so its complaining that you are doing stuff after the headers and that stuff might not happen.

---

### Post by Cappy on 2007-05-20
cookies must be set before any other data is sent. It is just the way it is.

---

