---
title: "Apache stopped, won't restart?"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by locoHost on 2006-09-17
I stopped Apache2 and now it won't restart. Here is my terminal win...

mark@d6games:~$ sudo /etc/init.d/apache2 stop
Password:
 * Stopping apache 2.0 web server...                                     [ ok ]
mark@d6games:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
mark@d6games:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
mark@d6games:~$


What happened?

---

### Post by kidders on 2006-09-17
Something is already bound to port 80 on your machine. You could use netstat to figure out what it is.

It's possible that it's merely a stray apache process ... **ps aux|grep apache** will tell you that.

---

### Post by locoHost on 2006-09-17
Ok, I had two instance of apache running. I think see terminal win...

mark@d6games:~$ sudo /etc/init.d/apache stop
 * Stopping apache 1.3 web server...                                     [ ok ]
mark@d6games:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]
mark@d6games:~$

So I stopped apache 1.3 but I still couldn't start apache2. What does that error mean?

---

### Post by locoHost on 2006-09-17
What does this tell me?...

mark@d6games:~$ ps aux|grep apache
root     11520  0.0  1.0  16880  5356 ?        Ss   13:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 11523  0.0  0.5  17012  3076 ?        S    13:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 11524  0.0  0.5  17012  3076 ?        S    13:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 11525  0.0  0.5  17012  3076 ?        S    13:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 11526  0.0  0.5  17012  3076 ?        S    13:34   0:00 /usr/sbin/apache2 -k start -DSSL
www-data 11527  0.0  0.5  17012  3076 ?        S    13:34   0:00 /usr/sbin/apache2 -k start -DSSL
mark     11645  0.0  0.1   2880   796 pts/0    R+   13:37   0:00 grep apache
mark@d6games:~$

---

### Post by jordanmthomas on 2006-09-17
You could kill the apache processes since they won't die themselves.
```
sudo kill {11523,11524,11525,11526,11527}
```
Then try restarting apache2

---

### Post by locoHost on 2006-09-17
Here is last terminal win...

mark@d6games:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (pid 11520) already running
                                                                                                    [ ok ]
mark@d6games:~$ sudo kill 11520
mark@d6games:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                                                    [ ok ]
mark@d6games:~$


What does this error mean?

---

### Post by jordanmthomas on 2006-09-17
I'm not sure what the error means exactly, but apache has started.
[http://localhost](http://localhost)
See?

---

### Post by locoHost on 2006-09-17
Yes, it seems to be started. Html files come up but not PHP. How do I start PHP? Yes, this is all very new to me :-D

---

### Post by jordanmthomas on 2006-09-17
Have you activated the php module for apache?
I really can't help you here...I had the same trouble for quite some time and I am not even sure how I fixed it.  I am not even close to being an apache expert.

Anyone else?

---

### Post by locoHost on 2006-09-17
When I type [http://localhost](http://localhost) in FF, I see a list of files and at the bottom is this...

Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80

That tells me Apache 2 is running AND PHP 5 is running. However, when I enter the URL of a PHP file that I know exists, Apache doesn't parse it, a file download starts. Can anyone determine what is happening?

---

### Post by jordanmthomas on 2006-09-17
I would be interested in the solution as well because of the troubles I've had with the same thing.

---

