---
title: "Simple /apache2.conf change: Limit connections to localhost"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-10
How do I do this?
Quoted from: [http://allyourtech.com/content/articles/16_01_2006_setting_up_a_local_web_server_in_debian_linux.php]("http://allyourtech.com/content/articles/16_01_2006_setting_up_a_local_web_server_in_debian_linux.php")
> If you'd like to play with a few of Apache's settings, the main configuration file is /etc/apache2/apache2.conf. Since by default Debian will allow external connections to Apache, you may want to limit connections to your localhost or local network only.

Thanks

---

### Post by DBStevens on 2007-06-11
Note the two sets of three lines after the the two sets of two lines that I commented out in the following
copy of /etc/apache2/sites-enabled/000-default .

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
#		Order allow,deny
#		allow from all
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
#		Order allow,deny
#		Allow from all
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
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

This restricts access to the local host for this rather simple setup.  This is one of many ways.

---

### Post by kasperbs on 2007-06-12
Thanks a lot, Just to make sure I have got it right here is my changes, could you verify them for me?
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
	Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
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

Thanks

---

### Post by DBStevens on 2007-06-12
You need to comment out the original Order, Deny, and Allow lines.

I have no idea what the configuration parser will do with the two sets for those changed directory containers.  I've never tried it that way.   It might work it might cause a hiccup when starting Apache.

Good luck.

---

### Post by kasperbs on 2007-06-13
Ok Thanks I have done that now, so it is exactly like yours.

Thank you very much again.

---

