---
title: "Apache2: How I reconfigure a website's root directory?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-19
By default, it seems that the root directory is [http://servername/apache2-default/](http://servername/apache2-default/)

What should I configure for the root directory to be at [http://servername/](http://servername/) (instead of /apache2-default) ?

Thanks !

---

### Post by jjn1056 on 2006-02-19
Off the top of my head I don't know the exact answer you are looking for (and I can't boot my distro right now while I am waiting for some thoughts on the problem I posted earlier today :) )  However:

There should be a readme file in /etc/apache2 that explains how debian lays out the configuration files.  It's a bit more complicated than the default apache2 conf file because they want to make it easier to automate adding and removing modules and sites.  Basically there is a directory in there where you put the conf files containing the location tags, etc.

Also there is an apache.conf file (or something named like that) in /etc/apache2 that should have a documentRoot tag in it. Take a look at that and see if it helps you.

If I can get back into my server I am sure I can give you a better answer.  good luck.

---

### Post by Akhran on 2006-02-19
This is what I have in /etc/apache2/sites-available/default
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
                # Commented out for Ubuntu
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

</VirtualHost>

```
I notice that if I uncomment "#RedirectMatch ^/$ /apache2-default/", I'm able to reach the default website at [http://servername](http://servername) instead of [http://servername/apache2-default](http://servername/apache2-default). However, my virtual directories are still reachable only via [http://servername/apache2-default/virtualdirectory](http://servername/apache2-default/virtualdirectory) instead of [http://servername/virtualdirectory](http://servername/virtualdirectory).

Any help would be appreciated.

Thanks !

---

### Post by jjn1056 on 2006-02-19
what do you have in your .../sites-enabled' directory?  This is the directory that gets parsed and included in the main apache2.conf 

Typically you put your site configuratation fragments in /sites-available and make a symbolic link in /sites-enabled to it so that you can turn the site on and off from the commandline easily.

(from inside sites-enabled)

like this ln -s ../sites-available mysite.conf

also, did you touch the apache2.conf file at all?

if you could attach both and let me take a look I might be able to help you.

---

### Post by Akhran on 2006-02-25
No changes have been made to the apache2.conf file. In the /etc/apache2/sites-available/default file, I made the following change:

```

DocumentRoot /var/www/

to 

DocumentRoot /var/www/apache2-default

```

So, now [http://servername](http://servername) (instead of [http://servername/apache2-default](http://servername/apache2-default)) is actually showing the default webpage :)

However, is this the recommended or correct way to achieve this? And, what is the purpose of having a apache2-default directory in /var/www/? Can't we just put the default webpages into /var/www ?

Thanks for the replies :)


[QUOTE=jjn1056]what do you have in your .../sites-enabled' directory?  This is the directory that gets parsed and included in the main apache2.conf 

Typically you put your site configuratation fragments in /sites-available and make a symbolic link in /sites-enabled to it so that you can turn the site on and off from the commandline easily.

(from inside sites-enabled)

like this ln -s ../sites-available mysite.conf

also, did you touch the apache2.conf file at all?

if you could attach both and let me take a look I might be able to help you.[/QUOTE]

---

### Post by Zeroangel on 2006-02-25
I suggest that you simply move the apache2-default directory out of your /var/www folder, and then going to [http://localhost/](http://localhost/) will simply read whatever is out of your /var/www folder instead of looking inside of the now non-existent apache2-default directory.

Put an index.html file inside of your /var/www folder if you don't want the internet to see all the subfolders inside of /var/www.

---

