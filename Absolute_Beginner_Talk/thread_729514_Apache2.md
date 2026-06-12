---
title: "Apache2"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by commondork on 2008-03-19
I'm attempting to learn LAMP.  I'm concentrating on the Apache aspect of LAMP at the moment.  Could someone direct me to a few understandable and informative guides or tutorials on using Apache2?  

I've looked through the apache2.conf file.  I know that /var/www/apache2-default is where the default web content is.  Could someone explain how to make /home/user/public_html the default when I browse to my IP?  Right now if I browse to [http://192.168.1.100/](http://192.168.1.100/) it simply shows a directory index with apache2-default as a link.

Any help getting me started would be greatly appreciated!

---

### Post by kaens on 2008-03-20
Their [docs]("http://httpd.apache.org/docs/2.0/") are good, but it can take awhile to find what you're liiking for. I can't think of any really good tutorials off the top of my head.

To change the default opening directory for apache, change DocumentRoot in your apache2.conf file.

---

### Post by justanotherhandle on 2008-03-20
Here's three on setting up a virtual host. That should get you started.

[http://www.techmongrel.com/05/setting-up-a-virtual-host-using-apache-2-on-ubuntu-710/](http://www.techmongrel.com/05/setting-up-a-virtual-host-using-apache-2-on-ubuntu-710/)
[http://www.linux.com/feature/118471](http://www.linux.com/feature/118471)
[http://www.unix-girl.com/geeknotes/apache_virtual_host_conf.html](http://www.unix-girl.com/geeknotes/apache_virtual_host_conf.html)

For specific (and general)  questions the apache2  online documentation is really good.
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

Good luck and have fun :)

HTH

---

