---
title: "[SOLVED] Apache Virtual hosts"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-05-15
Hello all, i have two domains that im trying to host on my Apache server, there are two files in /etc/apache2/sites-available

default:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@daveyonline.net
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
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

    <Directory "/var/www/phpmyadmin">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.1
    </Directory>

</VirtualHost>
```

and [www.daveyonline.info:](www.daveyonline.info:)

```
#
# Example.com (/etc/apache2/sites-available/www.example.com)
#
<VirtualHost daveyonline.info>
ServerAdmin webmaster@localhost
ServerAlias www.daveyonline.info

# Indexes + Directory Root.
DirectoryIndex index.html
DocumentRoot /var/www/daveyonline_info/

# CGI Directory
#ScriptAlias /cgi-bin/ /var/www/daveyonline_info/cgi-bin/
#<Location /cgi-bin>
# Options +ExecCGI
#</Location>


# Logfiles
ErrorLog /home/davey/logs/error.log
CustomLog /home/davey/logs/access.log combined
</VirtualHost>
```

My problem now is should i have put the contents of [www.daveyonline.info](www.daveyonline.info) in default?

am i doing something wrong as i both domains ([daveyonline.net]("http://www.daveyonline.net") & [daveyonline.info]("http://www.daveyonline.info")) show the same website...

any help would be much appreciated

Thanks, Davey

---

### Post by DaveyG on 2007-05-15
Bump...

---

### Post by foresth on 2007-05-15
The problem probably is that you haven't defined any ServerName in your 'default' virtual host. Try to add ```
ServerName www.daveyonline.net
``` or whatever domain you want into the default host. Also you don't need the ServerAlias with the same domain which the virtual host points to.

---

### Post by DaveyG on 2007-05-15
ah i see :D thanks il give that a try

---

### Post by DaveyG on 2007-05-15
> **foresth said:**
> The problem probably is that you haven't defined any ServerName in your 'default' virtual host. Try to add ```
ServerName www.daveyonline.net
``` or whatever domain you want into the default host. Also you don't need the ServerAlias with the same domain which the virtual host points to.

yay! it works, thank you so much! :D

---

