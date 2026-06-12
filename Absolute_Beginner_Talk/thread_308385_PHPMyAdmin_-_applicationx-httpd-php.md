---
title: "PHPMyAdmin - application/x-httpd-php"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by jran on 2006-11-28
I catn't call up phpmyadmin from my server. I keep getting asked to DL a file-type *application/x-httpd-php*. Can anyone help? 

Thanks,
jran

---

### Post by jran on 2006-11-28
Ok - I have been reading a lot of post about phpmyadmin and looking to see if anyone else has this problem too. I can't seem to find a fix for it.
I am running Breezy LAMP server and when I try to hit myserver/phpmyadmin/index.php from my XP box Firefox wants to download [this]("http://jasonnardi.com/22ni69ib.txt") file. 
It looks like this should load up in my browser, but it doesn't. Can anyone help?

TIA!
Jason

---

### Post by indytim on 2006-11-28
Have you tried:

[http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php)

?

IndyTim

---

### Post by jran on 2006-11-28
Thanks Tim, 
I have tried that using the server name and IP address. the browser still prompts my save a file...

Jason

---

### Post by mars17tv on 2006-12-07
I have the same problem :( , anyone have a solution?

---

### Post by thornomad on 2006-12-07
Are you able to view other .php files correctly on your server?  

It looks as if your server isn't executing the php code as it should ...

---

### Post by az on 2006-12-07
Install libapache2-mod-php5

See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by mars17tv on 2006-12-08
It's ok, libapache2-mod-php5 is needed
Thanx :)

---

