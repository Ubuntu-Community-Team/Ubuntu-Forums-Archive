---
title: "Can't ping / access Localhost"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by newbie289 on 2007-12-12
Hello

I have 3 computer home network (2-windows & 1 freshly installed Ubuntu Feisty Fawn 7.04) and inorder to make it as LAMP server I followed the instructions as stated here

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

The LAMP was up running fine. I saw apache running from other 2 windows machine (like [http://192.168.1.100/](http://192.168.1.100/)) and even acessed mysql and tested it. Later I installed PHPMyadmin successfully.

(P.S. Server IP is 192.168.1.100)

Things were fine untill  I rebooted the server. Later I cant access/ping the localhost. But all services are up and running fine.

Firefox states...

Request:  [http://localhost/](http://localhost/)
Error:
The connection has timed out
The server at localhost is taking too long to respond.
*   The site could be temporarily unavailable or too busy. Try again in a few moments.
*   If you are unable to load any pages, check your computer's network connection.
*   If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.


Request: [http://192.168.1.100/](http://192.168.1.100/)
Error:
The connection has timed out
The server at 192.168.1.100 is taking too long to respond.
*   The site could be temporarily unavailable or too busy. Try again in a few moments.
*   If you are unable to load any pages, check your computer's network connection.
*   If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.

~~~~~~~~~~~~~~~~~~~~~~~~~~~

I can still access [http://192.168.1.100/](http://192.168.1.100/) from other 2 windows machines.

What should I change in order to fix this.

Please help. I am very new to linux.

If u need any add' details, please let me know. I need to fix this up.

Thanks a ton in advance !!

---

### Post by Dr Small on 2007-12-12
Maybe apache never started at bootup. Try starting it.
```
sudo /etc/init.d/apache2 start
```

Dr Small

---

### Post by newbie289 on 2007-12-13
Nope Apache started during boot. 

though I tried ur statement after reboot

but 


 * Starting web server (apache2)...  
 httpd (pid 5655) already running
 [ OK ]

*************************************************************************

I doubt I need to alter some DNS or Bind or host files...... plz help

---

