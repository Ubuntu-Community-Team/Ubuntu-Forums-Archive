---
title: "Apache2 won't start  :("
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by drewsimon on 2006-11-04
Apache2 won't start up again. When I boot up my computer and go to 127.0.0.1 in my browser it gives an error. I tried 

[code]
$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                                                         [fail] 

[code]

Any tips?

](*,) ](*,) ](*,)

---

### Post by drewsimon on 2006-11-04
It's a brand new install of Edgy and I just installed all the components of a LAMP server using apt-get

---

### Post by bsussman on 2006-11-04
Look in the apache2 error log in /var/log/apache2

---

### Post by drewsimon on 2006-11-05
```

[Sat Nov 04 11:26:16 2006] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Sat Nov 04 11:26:30 2006] [notice] caught SIGTERM, shutting down
[Sat Nov 04 11:26:32 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sat Nov 04 11:27:16 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sat Nov 04 11:27:19 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:27:20 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:27:20 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:27:29 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:27:30 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:27:30 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:27:50 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:39:13 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:42:06 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:42:08 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:42:08 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sat Nov 04 11:42:24 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico

```

---

### Post by bsussman on 2006-11-05
> **drewsimon said:**
> ```

[Sat Nov 04 11:26:16 2006] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Sat Nov 04 11:26:30 2006] [notice] caught SIGTERM, shutting down
** [Sat Nov 04 11:26:32 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations**
[Sat Nov 04 11:42:08 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
.
.
.
[Sat Nov 04 11:42:24 2006] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico

```
That log extract shows me that Apache 2 is up and running.  
The favicon errors ( [http://www.wisegeek.com/what-is-a-favicon.htm](http://www.wisegeek.com/what-is-a-favicon.htm)  can be eliminated by putting a favicon in the indicated directory) don't matter.

I am not sure there is problem with apache.  The bolded message says Apache2 **will** start.  And assuming you pasted to the end, I see no failures

Do you get a page when you put localhost in your browser bar ( [http://localhost/](http://localhost/) )?  what about with [http://127.0.01](http://127.0.01) ?

---

### Post by drewsimon on 2006-11-05
When I put 127.0.0.1 or localhost into my browser, I get an error page. I don't know what I'm doing wrong. If try to restart apache2 using this command:
> 
sudo /etc/init.d/apache2 restart


I get this:
> 
* Forcing reload of apache 2.0 web server...                            [fail]


---

### Post by bsussman on 2006-11-05
Well that fail definitely means that apache2 is not happy.

But the log should show something.

I suspect config file.

You might try running ```
sudo apache2 -t -D DUMP_VHOSTS
``` which is a syntax check and  vhost config.

You might try running ```
sudo apache2 -X
``` which is debug mode - it will act like a normal program and might tell you something in the terminal you run it from.

---

### Post by drewsimon on 2006-11-05
Both
```
sudo apache2 -t -D DUMP_VHOSTS
```
&
```
sudo apache2 -X
```
result in:
> 
Syntax error on line 19 of /etc/apache2/sites-enabled/000-default:
</Directory>rom> directive missing closing '>'


---

### Post by drewsimon on 2006-11-05
I fixed that line of that  file and it works again! 

Thanks, bsussman!

---

### Post by bsussman on 2006-11-05
I think I am everyone...

Yer welcome.

Please change thread name to include the word 'solved'

---

