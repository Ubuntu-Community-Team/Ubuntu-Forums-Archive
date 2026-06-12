---
title: "protecting phpMyAdmin"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by timr92 on 2007-12-06
I'm trying to use .htaccess & .htpasswd to protect my phpMyAdmin installation. but apache seems to be ignoring these. I installed phpMyAdmin from source and have configured it, all is well but apache ignores my efforts to password protect that directory. I've read in other posts not to use .htaccess, but it seems if i do that i can only administer from my computer, but i'd like to be able to administer from anywhere.

---

### Post by hyper_ch on 2007-12-06
you must first give the directory where you have phpMyAdmin the permission to use overrides through .htaccess.

---

### Post by indytim on 2007-12-06
I believe that phpMyAdmin also has a password feature available as a front-end.  I don't use it as my local phpMyAdmin is 100% development.  You might want to swing over to their site for the pertinent details.

IndyTim

---

### Post by timr92 on 2007-12-06
and how do i do overrides thing, lol. soz i'm a linux noob. and have never used apache, only Abyss WS with PHP & MySQL, on win NT 4

---

### Post by hyper_ch on 2007-12-06
Have a read at the apache's "Allow Override" directive.

---

### Post by timr92 on 2007-12-06
i dont understand, and i just did something to /etc/apache2/sites-enabled/000-default and now apache wont work, what is the default contents of that file?

---

### Post by timr92 on 2007-12-06
I've managed to get apache starting again, but when i go to pma (the phpMyAdmin directory), in my browser, it says internal server error :D

Heres the 000-default file, is it ok?
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes All
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
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

---

