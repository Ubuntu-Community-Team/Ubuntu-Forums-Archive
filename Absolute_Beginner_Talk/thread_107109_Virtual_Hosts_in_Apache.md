---
title: "Virtual Hosts in Apache"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-12-22
Could someone post an example block of code they use for multiple virtual hosts in Apache?  I have done it with only one, and cannot get any more by just copying the code I put in.

Thank you.

---

### Post by gnu2tux on 2005-12-22
[QUOTE=amcavoy]Could someone post an example block of code they use 
for multiple virtual hosts in Apache?  I have done it with only one, and cannot get any more by just copying the code I put in.

Thank you.[/QUOTE]

Taken from a working example on an ubuntu 5.10 server (/etc/apache2/sites-enabled/default):

<VirtualHost *>
        ServerName domain.com
        ServerAlias [www.domain.com](www.domain.com)
        DocumentRoot /www/user/domain.com/html
        CustomLog /www/user/domain.com/logs/access_log combined
       ErrorLog /www/user/domain.com/logs/error_log
</VirtualHost>

I'm using bind 9 for dns.

Let me know how you get on!

---

### Post by amcavoy on 2005-12-22
I will try this, but I have two questions first:

1. Can I put this in my httpd.conf file?

2. If I need to add another, can I just copy the template you provided, change it around, and put it directly under my first virtual host?

Thanks for the help.

---

### Post by gnu2tux on 2005-12-22
[QUOTE=amcavoy]I will try this, but I have two questions first:

1. Can I put this in my httpd.conf file?

2. If I need to add another, can I just copy the template you provided, change it around, and put it directly under my first virtual host?

Thanks for the help.[/QUOTE]

1. I would imagine so, however, httpd.conf is obsoleted in ubuntu, so you would have to do a bit of poking around. I would stick the newer sites-enabled method, which is exactly the same format as httpd.conf, only easier to use for virtualhosting, as it doesn't have all the other mess in it. You can always add directives directly into that file if you want.

2. Correct.

HTH.

---

