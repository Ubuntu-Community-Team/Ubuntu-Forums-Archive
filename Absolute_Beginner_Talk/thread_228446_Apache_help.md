---
title: "Apache help"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by ragdemai on 2006-08-03
I having problem when I reload apache :
[Thu Aug 03 17:32:48 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                         [ ok ]
I gest my virtual host is not running

Someone can help? I new to apache.

Thankx

---

### Post by Kurt` on 2006-08-03
Maybe you can post the conf file that is causing the error?

Also, there is a [Server Chat](http://ubuntuforums.org/forumdisplay.php?f=45) section where your thread is less likely to be pushed off onto page 10 after an hour. :)

---

### Post by ragdemai on 2006-08-03
Hi Kurt`,
Thank you for your reply, below is my config file:

NameVirtualHost *
<VirtualHost 172.16.1.250:81>
	ServerName  joomla.com
        #ServerAlias joomla.com
        DocumentRoot /var/www/petranet
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/petranet/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>

---

