---
title: "Apache Virtual Server Index of /index.html"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-04-15
I have setup an Ubuntu Server and have gotten Apache to host my website - [www.Cerant.com](www.Cerant.com).

I tried to get Virtual Server to work so that I could use Squirrel Mail this way ...
mail.Cerant.com
... rather than this way:  [www.Cerant.com/squirrelmail](www.Cerant.com/squirrelmail)

Below is my /etc/httpd.conf:

NameVirtualHost 192.168.0.100

<VirtualHost 192.168.0.100>
        ServerName [www.Cerant.com](www.Cerant.com)
        DocumentRoot /var/www
</VirtualHost>

<VirtualHost 192.168.0.100>
        ServerName mail.Cerant.com
        ServerAlias mail
        DocumentRoot /var/www/squirrelmail
</VirtualHost>



When I browse to [www.Cerant.com/squirrelmail](www.Cerant.com/squirrelmail), it works.
Whan I browse to mail.Cerant.com all I get is a page with:

Index of /index.html
[ICO]	Name	Last modified	Size	Description
[DIR]	Parent Directory	 	-
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at mail.cerant.com Port 80

Anyone know why I cannot get Virtual Servers to work?

Thanks

Carl

---

### Post by cwmoser on 2008-04-15
Further information about this is that when I browse to mail.Cerant.com,
the browser seems to want to deliver an index.html page rather than Squirrel Mails index.php page.

Carl

---

### Post by cwmoser on 2008-04-15
Further explaining this, when I enter "mail.Cerant.com" in hte Address field of my browser, it self completes to:  [http://mail.cerant.com/index.html/](http://mail.cerant.com/index.html/)

If I modify the above slightly changing **index.html **to **index.php**  --  presto, I get the SquirellMail login page.

It appears that its something to do with Apache selecting the proper html file or php file.

Carl

---

### Post by cwmoser on 2008-04-15
Dummy me.  Squirrel Mail put in an empty folder named index.html.  After realizing that this was what the output was trying to tell me, I renamed the folder index.html to index.html-SAVE and now it works.

Duh.

Carl

---

