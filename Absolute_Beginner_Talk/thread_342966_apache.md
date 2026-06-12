---
title: "apache"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2007-01-20
I am new to apache on linux. my question is how do I start apache??

---

### Post by iluminate on 2007-01-20
Hi,
Have you installed it yet or not?
to start:
sudo /etc/init.d/apache2 start
to stop:
sudo /etc/init.d/apache2 stop
to restart:
sudo /etc/init.d/apache2 restart

---

### Post by RED WIND on 2007-01-20
ok that worked

tahnks

but now when I start it, it say could not determine the server's fully quilified domain name
and when I try to get to it using the ip I get a 403 forbidden error.

wut should I do???

---

### Post by RED WIND on 2007-01-20
bump

---

### Post by chalex on 2007-01-20
You will need to appropriately edit the apache config file.  It's probably /etc/apache2/httpd.conf or something like that.  It should be well commented, so just follow what it says.  If you need more info, here's the manual: [http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

---

