---
title: "Apache Security"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by pace_tua on 2005-06-23
I run a local webserver for developmental purposes only- its only for local access. Well, I know in MS Windows I had to be careful, hence a firewall amoung other things.

So my question is about security. If I were to give myself permission to create files in the [color=Sienna]/var/www[/color] folder, does this have any type of security issues associated with it?

---

### Post by Kvark on 2005-06-23
It would make /var/www/ exposed to the same security risks as your home directory. Anyone logged in as you or any program ran by your user account can edit it. Personally I changed the apache config files to use /home/kvark/www/ instead cause i hate going outside of home.



As for apache and security...

If you don't need anyone to access the webserver remotely then make apache listen on localhost only. No security holes open to the outside if it isn't even possible to connect to it from the outside ;)

Look for a line that says "Listen 80" in the apache config files. Change that to "Listen 127.0.0.1:80". That line is in /etc/apache2/ports.conf.

---

### Post by pace_tua on 2005-06-23
[QUOTE=Kvark]Personally I changed the apache config files to use /home/kvark/www/ instead cause i hate going outside of home.[/quote]
  Yea...
[QUOTE=Kvark]Look for a line that says "Listen 80" in the apache config files. Change that to "Listen 127.0.0.1:80". That line is in /etc/apache2/ports.conf.[/QUOTE]
Oo. Thanks for that tip.

---

### Post by heart_reaver on 2005-06-24
you can use help of 

[www.debian-administration.org](www.debian-administration.org)

here you can find lots of admin stuff.

 \\:D/

---

### Post by ad noiseam on 2005-11-08
[QUOTE=Kvark]If you don't need anyone to access the webserver remotely then make apache listen on localhost only. No security holes open to the outside if it isn't even possible to connect to it from the outside ;)

Look for a line that says "Listen 80" in the apache config files. Change that to "Listen 127.0.0.1:80". That line is in /etc/apache2/ports.conf.[/QUOTE]

I did just this after reading [url=
https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=(mysql)]this Wiki article[/url].

Everything works fine, but when I include this "Listen 127.0.0.1:80", I can not browse my data on var/www in my browser anymore. Firefox tells me "The connection was refused when attempting to contact Localhost", even though I am on the very same machine... :-(

---

