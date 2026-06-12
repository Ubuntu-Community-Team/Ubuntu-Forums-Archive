---
title: "no vhost dir in ubuntu?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by spcoex on 2007-10-21
hi all, 

i just noticed that unlike my redhat server, i dont see any vhosts directory in my ubuntu (feisty) server? I think has something to do with activating some sort of "host based" parameter in httpd.conf...??
does this mean I can only host ONE domain?? what do I need to do to host more than one domain?

---

### Post by llamakc on 2007-10-21
Enable it in /etc/apache2/sites-available and link to it in /etc/apache2/sites-enabled.

---

### Post by spcoex on 2007-10-22
thanks llamack. 
I opened the default text file in /etc/apache2/sites-available, what line do I edit to enable it?
And what is meant by "link to it".....do I create a symbolic link? 

Thank
spcoex

---

### Post by spcoex on 2007-10-23
Does anyone have a simple document explanining how I can enable vhost on my apache?

---

### Post by llamakc on 2007-10-23
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

---

