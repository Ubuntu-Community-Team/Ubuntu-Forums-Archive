---
title: "how to make a link localhost/mySite in apache2 ??"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-04-12
I have Ubuntu 6.10 Edgy Eft and Apache2 Webserver running.

I have a website under my eclipse/workspace directory which I would like to reach like this:

[http://localhost/mySite](http://localhost/mySite)

At the moment, I have made an entry in /etc/apache2/sites-available/mySite like this:

---------------------------------------------------------

#FILE: /etc/apache2/sites-available/mySite

NameVirtualHost mySite:80

<VirtualHost mySite:80>
	ServerAdmin ahlandberg@localhost
	ServerName mySite
	
	#DocumentRoot /srv/www/htdocs
	DocumentRoot /home/ahlandberg/eclipse/workspace/mySite
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
#	<Directory /srv/www/htdocs>
#		Options Indexes FollowSymLinks MultiViews
#		AllowOverride None
#		Order allow,deny
#		allow from all
#		# Uncomment this directive is you want to see apache2's
#		# default start page (in /apache2-default) when you go to /
#		#RedirectMatch ^/$ /apache2-default/
#	</Directory>

	<Directory /home/ahlandberg/eclipse/workspace/mySite>
		Options FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
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


--------------------------------------------

Also, in the /etc/hosts file, I have the following entry:

--------------------------------------------

127.0.0.1 localhost.localdomain localhost mySite
#127.0.0.1 localhost
127.0.1.1 ubuntu610

--------------------------------------------

This enables me to access the "mySite" in the browser under [http://mySite](http://mySite)


If somebody has an idea how to fix it, thank you very much in advance!!!

Anders

---

### Post by justleen on 2007-04-12
by creating a folder/symlink in /var/www/MySite

---

### Post by darkrose on 2007-04-12
in /etc/apache2/apache2.conf

add this line:

Alias /mySite/ "/home/ahlandberg/eclipse/workspace/mySite/"

and restart apache
/etc/init.d/apache2 restart

[http://localhost/mySite](http://localhost/mySite) will now point to /home/ahlandberg/eclipse/workspace/mySite/

HTH

---

### Post by ahlandberg on 2007-04-12
Hi again.

I added the line to the apache2.conf file and left all my other settings. However, the problem still remains. When I go to [http://localhost/mySite](http://localhost/mySite) it cannot find it, but [http://mySite](http://mySite) still works.

I found this link: [http://www.howtogeek.com/howto/ubuntu/make-a-backup-copy-of-your-production-wordpress-blog-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/make-a-backup-copy-of-your-production-wordpress-blog-on-ubuntu/)

and followed some of the instructions there:

We’re going to imagine that your site root directory is now in /home/username/wordpress/ for the purposes of this article. If you’ve extracted it elsewhere, then substitute accordingly. We need to add in the alias into apache, so open up the following file:

    /etc/apache2/conf.d/alias

You’ll want to paste in these lines, and adjust the paths according to your system and the /directory you want the test blog to be available on.

    Alias /wordpress /home/username/wordpress
    <Directory /home/username/wordpress>
    Options Indexes FollowSymLinks
    AllowOverride All
    Order allow,deny
    Allow from all
    </Directory>

Restarted apache with

sudo apache2ctl restart

and [http://localhost/mySite](http://localhost/mySite) works!

---

