---
title: "start apache"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by dujlinvik on 2006-12-29
greetings,
i'm new in web development, just installed Apache in Ubuntu. I've been using apache in windows, there is a executable program icon for Apache to start the server. How can I find out in Ubuntu if my Apache is running?
i copied my site (php) into ....apache2/htdocs/  but in browser i only get one of these 2 "outputs" :
1. UNABLE TO CONNECT
2. "Forbidden
    You don't have permission to access /mysite/index.php on this server."

Thanks in advance, regards

---

### Post by KenSentMe on 2006-12-29
First of all, how did you install apache on Ubuntu, via Synaptic? If not, do so, because that's the best way to install all sofware, and Apache too. What version of apache do you use?

Apache is started by running: 'sudo /etc/init.d/apache(2) start' if you installed it with apt or synaptic. Normally apache is started at boot time, so you don't have to start it manually.

Check here for more info on installing Apache2, PHP and Mysql on Ubuntu: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by az on 2006-12-29
Apache is started when you boot.


The default site is in /var/www.

---

### Post by dujlinvik on 2006-12-29
i've installed Apache 2.2 in that "Terminal thing...", everything seems to be OK. I've installed it into /usr/local/apache2 .
i have no idea why firefox can't open anything from the htdocs folder, i tried to copy my site into /var/www, with same results.... 
any ideas?
regards

---

### Post by KenSentMe on 2006-12-29
> **dujlinvik said:**
> i've installed Apache 2.2 in that "Terminal thing...", everything seems to be OK. I've installed it into /usr/local/apache2 .
i have no idea why firefox can't open anything from the htdocs folder, i tried to copy my site into /var/www, with same results.... 
any ideas?
regards

Believe me, you'de better install it with apt or synaptic. This way all settings a optimal for Ubuntu and it's easy to install PHP, MySQL etc. If there is a package for a certain program in the repositories it's always better to install that one, instead of a manual install, unless you have a good reason to do the install by yourself.

Read the wiki page at the link i gave you in my previous post.

---

### Post by dujlinvik on 2006-12-29
i appreciate Your help, and off course i believe You :) 
Do I need to unistall/remove my previously installed apache? How can i do that?
thanks
regards

---

