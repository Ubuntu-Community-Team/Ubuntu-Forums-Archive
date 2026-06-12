---
title: "PHP in APACHE"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by hechizera on 2007-06-23
hi,

can you tell me how to enable php module in apache? please :(

---

### Post by hechizera on 2007-06-23
:(

---

### Post by octoberdan on 2007-06-23
> **hechizera said:**
> hi,

can you tell me how to enable php module in apache? please :(

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server)

Good luck. Let us know if you have any questions or need further help.

---

### Post by hechizera on 2007-06-23
> **octoberdan said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server)

Good luck. Let us know if you have any questions or need further help.

thanks for your reply, octoberdan! I just did all of the steps as in the manual, but when I restart apache i have these lines:
```

xxxxxxxx@xxxxxxxx:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                   
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, 
using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```
plus when I try to launch phpmyadmin in the browser it offers to open or save some .phtml file. what's wrong with the php and apache if I follow step-by-step instructions? :(

---

### Post by az on 2007-06-23
Do you have another version of apache running?  (do you have apache and apache2 installed?)  You should only have apache2 installed.

If not that, something else is preventing apache2 from using port 80.  Are you running skype on this computer?   Skype uses port 80 as well.

---

### Post by hechizera on 2007-06-23
> **az said:**
> Do you have another version of apache running?  (do you have apache and apache2 installed?)  You should only have apache2 installed.

If not that, something else is preventing apache2 from using port 80.  Are you running skype on this computer?   Skype uses port 80 as well.
no, I don't use skype. I just found that I have apache and apache2. ok, I removed apache. now when I try to reload apache2  I see only this message:
```

xxxxxxxxx@xxxxxx:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...                                                                          [ OK ] 
xxxxxxxxx@xxxxxx:~$ 
```
and when I try to reach localhost in the browser, it doesn't open at all! it says -unable to connect! omg this apache and php looks like mission impossible :cry:

---

### Post by hechizera on 2007-06-23
yes! yes I did it!! it works!! :D:D:D thanks everyone for help!

So what did I do!
1) I  removed everything related to php, mysql and apache through Synaptic

2) then I used this link [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server)
I've installed apache2, php and mysql again.

3) then I  used this one: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)  after I received:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

4) cleared the cache
that's it! now I don't have this annoying .phtml file and everything works fine :D:D:D

---

### Post by az on 2007-06-23
> **hechizera said:**
> 
that's it! now I don't have this annoying .phtml file and everything works fine :D:D:D

W00t!  

The trouble is that a lot of guides give slightly wrong information.  The end result is that you can have both apache and apache2 installed at the same time.  To make matters worse, you can end up with libapache-mod-php5 instead of libapache2-mod-php5 and end up with a problem that is not so easy to spot.

---

