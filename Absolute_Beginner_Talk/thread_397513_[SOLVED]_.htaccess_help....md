---
title: "[SOLVED] .htaccess help..."
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-30
Ok so first i enabled AllowOveride in /etc/apache2/sites-available/default

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin Webmaster@Daveyonline.net
	
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		[COLOR="Red"]AllowOverride All[/COLOR]
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		[COLOR="Red"]AllowOverride All[/COLOR]
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Restarted Ubuntu (as i dont know the command to restart apache) 
created a .htaccess file, chmod 755 /var/www/.htaccess using the terminal,
then added ```
Redirect 301 /test.html http://www.ubuntuforums.org
``` to the .htaccess file, tested [http://www.daveyonline.net/test.html](http://www.daveyonline.net/test.html) and it doesnt seem to redirect... im guessing .htaccess hasnt been set up properly?..

Any help would be much appreciated.

Thanks, Davey


Edit: Should .htaccess be in /var/www/.htaccess? or /var/.htaccess?

---

### Post by DaveyG on 2007-03-30
Bump...

---

### Post by MikeDX on 2007-03-30
> **Davey Goudou said:**
> Bump...

a bump after only 12 minutes :o

anyways.. i do believe .htaccess should be in the same dir as your files, so for the root of your own server this will be /var/www or for your own user directory ~/public_html

to restart apache, go to a terminal window and type: 

sudo /etc/rc.d/apachectl restart


Mike

---

### Post by DaveyG on 2007-03-30
> a bump after only 12 minutes :o

Yea i was in a hurry to get this sorted :) 

> 
anyways.. i do believe .htaccess should be in the same dir as your files, so for the root of your own server this will be /var/www or for your own user directory ~/public_html

to restart apache, go to a terminal window and type: 

sudo /etc/rc.d/apachectl restart


Mike

Thank you so much for your help, its all fixed.

---

