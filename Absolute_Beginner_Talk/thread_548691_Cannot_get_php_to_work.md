---
title: "Cannot get php to work"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by New Boy on 2007-09-11
I set up Feisty a couple of weeks ago and at that time I installed LAMP.  All seemed to work OK; at least [http://localhost/apache2-default/](http://localhost/apache2-default/) opened up with "It works!". And it still does.  But nothing else works.

I added <?php phpinfo(); ?> into testphp.php which did work originally but now a window comes up asking me "What should Firefox do with this file" Entering "Open with Firefox" just opens up another Firefox window with the same results.

Exactly the same happens with phpmyadmin.

Can any-one advise please.

I can't recall what I've done over the last few weeks. I have installed some programs and deleted some - including backuppc which wants to use the web server - I didn't like it so I deleted it. (Least I thought I had but backuppc still keeps appearing in Groups - even though I keep deleting it.)

I also wondered why some groups have group members ticked and some don't - group mysql has both root and myself ticked - is that correct - I've tried unticking but that hasn't made any difference.

Help would be appreciated please.

Thanks

New boy

---

### Post by Clay_Banger on 2007-09-12
how are you accessing these files? u need to access them via a http url for them to work correctly.

so in firefox, it should look like:
```
http://localhost/phpinfo.php
```
instead of:
```
file:///path/to/file/phpinfo.php
```

the latter one will produce a message like what you describe.

---

### Post by Koybe on 2007-09-12
Could you check you have all the needed package for your LAMP server?

```
sudo apt-get install apache2 libapache2-mod-php5 php5-mysql mysql-server
```

---

### Post by bikeboy on 2007-09-12
php5 module enabled?

```
ls -l /etc/apache2/mods-enabled/
```

---

### Post by gvoima on 2007-09-12
Yes indeed, I also installed LAMP server some time ago and I had to enable the PHP module.
So be sure it's enabled :)

---

### Post by New Boy on 2007-09-12
Thank you for your reply - sorry for the delay, I've only just got back to my computer.

> **Clay_Banger said:**
> how are you accessing these files? u need to access them via a http url for them to work correctly.

so in firefox, it should look like:
```
http://localhost/phpinfo.php
```



Yes, that is how I'm accessing it.

[http://localhost/](http://localhost/)
produces an index of 3 items:
apache2-default/	20-Nov-2004 20:16 	-
phpmyadmin/	24-Mar-2007 23:47 	-
testphp.php	20-Aug-2007 20:13 	20

The first one produces a web page saying "It works!"
The other two bring up a message window asking me what I want to do with it.

David

---

### Post by hyper_ch on 2007-09-12
if you called your file testphp.php then you cannot access it by phpinfo.php

---

### Post by New Boy on 2007-09-12
Thank you for your reply.  Sorry for the delay - I've only just got back to my computer.

> **Koybe said:**
> Could you check you have all the needed package for your LAMP server?

```
sudo apt-get install apache2 libapache2-mod-php5 php5-mysql mysql-server
```

Well! something was obviously missing - because after doing that, it all works as expected.

Many thanks for your help.

---

### Post by New Boy on 2007-09-12
Thank you to all those who replied. 

It now works as expected - see earlier replies.

David

---

### Post by wordsmythe on 2007-09-21
It seems that the "one-step" LAMP install package doesn't install mysql-server.

I'm having a similar issue, though that doesn't seem to have been enough to solve it for me. :\

Oh well, time to keep working!

(PS: Whew, it's been a long time since I last posted here!)

---

### Post by hyper_ch on 2007-09-22
installing mysql:

```

apt-get install mysql-server mysql-client libmysqlclient15-dev

```

installing apache2
```

apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 ssl-cert

```
```

apt-get install libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php5-idn php-pear php5-imagick php5-imap php5-json php5-mcrypt php5-memcache php5-mhash php5-ming php5-mysql php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl

```

Taken from this extensive guide on how to setup a server in an ISP style:

[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

