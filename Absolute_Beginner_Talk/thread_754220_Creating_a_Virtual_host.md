---
title: "Creating a Virtual host"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by goldenbough on 2008-04-13
I am attempting to create a virtual host here on my machine.  I assume the place do this is in the /etc/apache2/sites-enabled/000-default file.  The file currently reads this:  

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



This is the information I am want to put in the host:

<VirtualHost 192.168.0.80>
 ServerName phpweb20
 DocumentRoot /var/www/phpweb20/htdocs

<Directory /var/www/phpweb20/htdocs>
  AllowOverride All
 Options All
</Directory>

php_value include_path .:/var/www/phpweb20/include:/usr/local/lib/pear
php_value magic quotes_gpc off
php_value register_globals off
</virtualHost>





So I changed the file to this:

NameVirtualHost *
<VirtualHost 192.168.0.80>
	ServerAdmin webmaster@localhost
        ServerName phpweb20
	
	DocumentRoot /var/www/phpweb20/htdocs
	<Directory />
		Options All
		AllowOverride All
	</Directory>
	<Directory /var/www/phpweb20/htdocs>
		Options All
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
php_value include_path .:/var/www/phpweb20/include:/usr/local/lib/pear
php_value magic_quotes_gpc off
php_value register_globals off

</VirtualHost>


When I restart apache in the terminal I get this message:  

 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Apr 13 12:26:55 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Apr 13 12:27:05 2008] [warn] NameVirtualHost *:0 has no VirtualHosts

---

### Post by wesleybailey on 2008-04-13
Copy the default file, and rename it in the same directory. Modify the fields you want to change. Then remove NameVirtualHost * from the top of the copied file. The "NameVirtualHost *" should only be mentioned once.

Let me know if that helps.


```

<VirtualHost 192.168.0.80>
ServerAdmin webmaster@localhost
ServerName phpweb20

DocumentRoot /var/www/phpweb20/htdocs
<Directory />
Options All
AllowOverride All
</Directory>
<Directory /var/www/phpweb20/htdocs>
Options All
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
php_value include_path .:/var/www/phpweb20/include:/usr/local/lib/pear
php_value magic_quotes_gpc off
php_value register_globals off

</VirtualHost>
```

BTW. If you want to get rid of the error "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName".
Put the following line in /etc/apache2/httpd.conf ```
ServerName NameMe
```

---

### Post by goldenbough on 2008-04-14
Adding the command line ServerName NameMe did help out with that one error.  Now when I changed the 000-default file with the code you provided, the server simply gives me an error when I open it through localhost.  When I try [http://phpweb20](http://phpweb20) it redirects to somebody's website htttp://www.phpweb20.com

---

### Post by spiderbatdad on 2008-04-14
have you enabled the site with:```
sudo a2ensite yoursite
``` where 'yoursite' is the name of the folder you used in sites-available, when renaming the default site?
Also, the directory should not be in your root file system. 
This is a good guide for getting started. [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Obviously, you don't need everything there, but the sections pertinent to your needs are there.

---

### Post by goldenbough on 2008-04-14
sudo a2ensite phpweb20


It responds "This site does not exist!"

---

### Post by spiderbatdad on 2008-04-14
In the folder /etc/apache2/sites-available you should have two files: one is 000-default...the other should be a model of the default file, but renamed, and with your specific virtual host settings.
sudo a2ensite (name of renamed file.)

---

### Post by goldenbough on 2008-04-15
Well I wasn't formatting that sites-enabled folder properly.  The site has been enabled, though when I input [http://phpweb20](http://phpweb20), it redirects to someone's website [http://www.phpweb20.com](http://www.phpweb20.com).

---

### Post by spiderbatdad on 2008-04-15
If you have enabled port forwarding on your router, you are likely prepared to receive http requests.
try just putting in your actual ip address...get it here [www.whatismyip.com](www.whatismyip.com)

If you have not enabled port forwarding but want to see if your page is displaying properly. just type localhost into the browser address...or your local ip...get it from ifconfig.

To be able to navigate through http request by name...you will need to establish an account with a DNS...like dyndns...which offers free naming service...but it has to be appended with one of their existing accounts like: podzone, or end-of-internet, for the free service

---

### Post by spiderbatdad on 2008-04-15
Actually for a php page try```
http://localhost/testphp.php
```

I recommend re-reading the link I provided previously and starting with an html page in your home directory. Then move on to displaying the /testphp.php page.

---

### Post by goldenbough on 2008-04-15
Thanks

---

### Post by babajc on 2008-05-04
Do you still have the following error message:
[warn] NameVirtualHost *:0 has no VirtualHosts

If so, see if this post helps:
[http://apachehelp.blogspot.com/2008/05/named-virtual-hosts-in-apache2.html](http://apachehelp.blogspot.com/2008/05/named-virtual-hosts-in-apache2.html)

---

