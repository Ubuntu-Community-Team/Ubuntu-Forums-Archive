---
title: "setting apache/php folders"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-07-14
just wondering if i can add a folder for apache/php to be parsed through the browser...

here's what i want, i got wamp running on vista and i want my LAMP to add the www folder on the wamp on my windows partition so that when i go localhost/...windows partition/www/ than it will bring up my index page... and parse php scripts as well...

---

### Post by DBStevens on 2007-07-14
If your lamp Stack is using Apache2 you have to change the DocumentRoot and the <Directory> containers in /etc/apache2/sites-enabled/000-default  to match up to your WAMP directory structure.

You also must add the files php5.conf and php5.load to the /etc/apache2/mods-enabled/  directory, these may be found in the /etc/apache2/mods-available/ directory.

Then you can restart Apache2.

---

### Post by manuleka on 2007-07-16
so here's my default file
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
......


```
do i need change both 
            DocumentRoot /var/www/ and <Directory /var/www/>
lines to /my/new/wamp/dir/www ??

---

### Post by DBStevens on 2007-07-16
I did.  

I didn't want to investigate the entire default setup.

Oh you might want to add the -Indexes to Options for the / directory and change the Indexes to -Indexes in the /var/www/  container.

Allowing automated directory listings is an information leak issue for internet facing  websites. 

Good luck.

---

