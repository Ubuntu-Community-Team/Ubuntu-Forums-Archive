---
title: "any all in one apache+PHP+MySQL package available for linux?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-06
Hi
Thank you for reading my post
there are several all in one package for windows which allows us to easily stop, start and maintaing mysql+apache+php.
is there something similar for Ubuntu?

Thanks

---

### Post by dynamethod on 2008-02-06
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

check that out dude, it has apache/php/mysql preinstalled

---

### Post by cb951303 on 2008-02-06
why is that needed? you can install all of them through apt-get with a single line

---

### Post by dynamethod on 2008-02-06
yeah and you can do that too lol

---

### Post by NeoGreen on 2008-02-06
I usually download the server version of Ubuntu.  During install you get the option to install LAMP version which as all those programs on one quick install.

---

### Post by jaytek13 on 2008-02-06
There isn't really a single command, but here's a short guide that has everything up and running in about 10 minutes.

[http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

---

### Post by legolas_w on 2008-02-07
I installed Apache, MySql and PHP now what?
Where are they installed? 
where I can check the status of Apache or Mysql?
How I can start and stop them?



Thanks

---

### Post by louieb on 2008-02-07
Good stuff here on setting up and using LAMP [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

I followed that and got a DYNDNS account. [Lou's Home Server Stuff]("http://louieb.isa-geek.net/") runs on a PC in my den.

Also look at phpmyadmin for managing MYSQL. (its in the repositories)
And [Webmin]("http://www.webmin.com/") for general server administration.

---

### Post by cb951303 on 2008-02-08
> **legolas_w said:**
> I installed Apache, MySql and PHP now what?
Where are they installed? 
where I can check the status of Apache or Mysql?
How I can start and stop them?



Thanks

you might wanna take a look to the links posted and to the wiki. I don't think anyone will bother REexplaining these to you since they are very well documented more then once in the wiki :)

---

### Post by hyper_ch on 2008-02-08
> **legolas_w said:**
> I installed Apache, MySql and PHP now what?
Where are they installed? 
where I can check the status of Apache or Mysql?
How I can start and stop them?



Thanks

```

ps aux | grep apache

```


```

ps aux | grep mysql

```

---

### Post by andrewjoy on 2008-02-08
Its not all in one but this is the one you want to look at.

It works relay well as you can see hear


[www.andrewjoy.co.uk](www.andrewjoy.co.uk)

oh and its not finished yet i just did that in about 15 mins to get sum thing up there

EDIT 

helps if i post the link lol

[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28my%29%7C%28sql%29](https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28my%29%7C%28sql%29)

---

### Post by jd65pl on 2008-02-09
Hey, here is a link to setting up your own web server

[http://jamiedumbill.com/index.php?page=37](http://jamiedumbill.com/index.php?page=37)

---

