---
title: "Apache2 errors"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by apocalypsxx on 2008-03-09
Hi.1st post & hello to everyone. =  ]

I just installed apache2 & all seemed to go well..
But when I run apache I get these errors! 



blah@blah:~$ apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:8080
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8080
no listening sockets available, shutting down
Unable to open logs
blah@blah:~$ 

------------------------------------------------
Listen 8080

<IfModule mod_ssl.c>
    Listen 443
</IfModule> 
------------------------------------------------

this my port.conf & it`s my guess this where the problem lies..
but really not sure what..

---

### Post by The Titan on 2008-03-09
> **apocalypsxx said:**
> Hi.1st post & hello to everyone. =  ]

I just installed apache2 & all seemed to go well..
But when I run apache I get these errors! 



blah@blah:~$ apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:8080
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8080
no listening sockets available, shutting down
Unable to open logs
blah@blah:~$ 

------------------------------------------------
Listen 8080

<IfModule mod_ssl.c>
    Listen 443
</IfModule> 
------------------------------------------------

this my port.conf & it`s my guess this where the problem lies..
but really not sure what..
i think the server is already running, have you tried connecting to localhost?  you can stop it by doing
```
 /etc/init.d/apache2 stop
```
start it by doing
```
/etc/init.d/apache2 start
```
and restart it with
```
/etc/init.d/apache2 restart
```

off-topic: Thats funny how it stuck those faces in there haha

---

### Post by apocalypsxx on 2008-03-09
Hi The Titan just tried your suggestions...after closing down & restarting
got this..
------------------------------------------------
blah@blah:~$ /etc/init.d/apache2 start
open: Permission denied
 * Starting web server apache2                                                  install: cannot change owner and/or group of `/var/lock/apache2': Operation not permitted
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:8080
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8080
no listening sockets available, shutting down
Unable to open logs
open: Permission denied

---

### Post by apocalypsxx on 2008-03-09
ok ok so I forgot the sudo command...
hehe!!
:)

now I get this..
-------------------------------------------------
blah@blah:~$ sudo/etc/init.d/apache2 start
bash: sudo/etc/init.d/apache2: No such file or directory
n30@n30:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
blah@blah:~$

---

