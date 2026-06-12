---
title: "Apache on Ubuntu 7.10 LAMP install"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by apidya on 2007-11-30
Hey all,

I'm moving my websites from one server to a new Ubuntu 7.10 server, I went with the default LAMP set up during installation and I am having trouble with finding apache configurations.

On my old fedora box the configuration was held in etc/httpd/httpd which I think is now etc/apache2/apache2.conf.  I am having trouble locating some of the paramaters, such as the DocumentRoot.  Am I looking in the wrong place.

Any help would be greatly appreciated.

---

### Post by MossKiller on 2007-11-30
In Ubuntu's set-up the configurations are separate for each 'site'. You'll find 'DocumentRoot' in '/etc/apache2/sites-available/default'.

---

