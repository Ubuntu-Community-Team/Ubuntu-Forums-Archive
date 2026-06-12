---
title: "Apache Question Config Issue"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by salaberrios on 2008-01-11
I pull up a web page on my web server and I keep getting the "Index of" page with the links to the web sites in my apache2 folder. How do I get the web site's index page to come up? Any help is appreciated.

---

### Post by Austin17 on 2008-01-11
Just put your index file in /var/www/

That is the default location apache2 looks at I think.

---

### Post by salaberrios on 2008-01-11
I don't think it looks for the index file there, it lookd for the site there...However, this started when I updated to 7.10 so who knows. Thanks. I'll give it a try but I am not certain that is it.

---

### Post by salaberrios on 2008-01-11
Anybody?

---

### Post by salaberrios on 2008-01-11
I pull up a web page on my web server and I keep getting the "Index of" page with the links to the web sites in my apache2 folder. How do I get the web site's index page to come up? Any help is appreciated.

---

### Post by Dr Small on 2008-01-11
Do you have this in your httpd.conf file ?
```
# DirectoryIndex: sets the file that Apache will serve if a directory
# is requested.
#
<IfModule dir_module>
    #DirectoryIndex index.html
    # XAMPP
    DirectoryIndex index.html index.html.var index.php index.php3 index.php4
</IfModule>
```

---

### Post by Clickbg on 2008-01-11
Remove file welcome.conf from your conf.d directory :)

---

### Post by salaberrios on 2008-01-11
No, I don't. That file is empty, shows nothing. This started after I upgraded a couple days ago. Should i place those entries into the file?

---

### Post by salaberrios on 2008-01-11
I don't see a file named welcome.conf. Only Apache2-doc, Nagios, phpmyadmin, and charset

---

### Post by OffAxis on 2008-01-11
depends on your setup...
For a single site you could 
put an index.html or index.php file in that folder

For multiple sites (or just a single)
you could
modify** /etc/apache2/vhosts.conf** file (if you're using that)
or modify your site specific .conf files in **/etc/apache2/sites-available** (if you're using that)
or modify **/etc/apache2/apache2.conf** (if you're using that)

If you overwrote the .conf file on an upgrade then it's probably the apache2.conf file that got changed.

---

### Post by Clickbg on 2008-01-11
Try to put this 

<Directory "/path/to/your/web/site">
  DirectoryIndex index.php index.html
  AllowOverride Limit AuthConfig
</Directory>

in httpd.conf or in file ending with .conf in your conf.d. If this does not do the job, post your httpd.conf

---

### Post by salaberrios on 2008-01-11
the httpd.conf is empty. Nothing. This issue just happend after I upgraded..7.10

---

### Post by OffAxis on 2008-01-11
did you try the apache2.conf?

Each site's .conf file should really go in 
**/etc/apache2/sites-available/[sitename].conf**
and then be activated with 
```
a2ensite
```

but for a quick edit you can just append your site to the bottom of the apache2.conf

---

### Post by salaberrios on 2008-01-11
I placed it in the only .conf file in the conf.d folder. I pasted the line sin teh phpmyadmin.conf below:

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php index.html
	AllowOverride Limit AuthConfig

	# Authorize for setup
	<Files setup.php>
	    # For Apache 1.3 and 2.0
	    <IfModule mod_auth.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    # For Apache 2.2
	    <IfModule mod_authn_file.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    Require valid-user
	</Files>
	<IfModule mod_php4.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
</Directory>

---

### Post by irv on 2008-01-11
Very simple, just create a index.html file in the root of your www directory. This will display instead of the index of files.
I tried this on my web server and it works. I am going to delete this file because I want the index of files for my use.
Irv

---

### Post by salaberrios on 2008-01-11
What is the command to enable a site? I did this yesterday and it said the site already exists. Also, how do I uninstall Apache? I want to try that as well.

---

### Post by salaberrios on 2008-01-11
> **irv said:**
> Very simple, just create a index.html file in the root of your www directory. This will display instead of the index of files.
I tried this on my web server and it works. I am going to delete this file because I want the index of files for my use.
Irv

Ok Irv, That worked, but here are a few questions:
why isn't pulling the Index file from the site folder location?
It pulls up the index file but all the pictures won't show up now. I know why that is, but I can't copy all of teh files to the www directory. Suggestions?

What about when I host another site?:confused:

---

### Post by irv on 2008-01-11
> **salaberrios said:**
> What is the command to enable a site? I did this yesterday and it said the site already exists. Also, how do I uninstall Apache? I want to try that as well.

Do you have your own server?
Do you have a registered Domain name?
There is no command to enable a site, you just need to publish one on your server and type you domain name in your web browser. Don't forget you need to bind your ip address to the domain name. This has to be done with whom ever you have your domain registered with.

---

### Post by irv on 2008-01-11
> **salaberrios said:**
> Ok Irv, That worked, but here are a few questions:
why isn't pulling the Index file from the site folder location?
It pulls up the index file but all the pictures won't show up now. I know why that is, but I can't copy all of teh files to the www directory. Suggestions?

What about when I host another site?:confused:
Put them in a image directory in the www directory and change your html code to point to them. It is call organizing your file on your site. If you wanted to keep you entire site in a separated directory, then you would have to type in your browser: [http://www.domain](http://www.domain) name/directory name.

---

### Post by salaberrios on 2008-01-11
> **irv said:**
> Do you have your own server?
Do you have a registered Domain name?
There is no command to enable a site, you just need to publish one on your server and type you domain name in your web browser. Don't forget you need to bind your ip address to the domain name. This has to be done with whom ever you have your domain registered with.

I do have my own server, I was asking what is the full command to run ap2ensite.

---

### Post by salaberrios on 2008-01-11
If you change the DocumentRoot in the default file in sites-available to point to the directory, that will save you from have to make all the changes you listed.:wink:

However, this doesn't quite solve the multiple site issue. I assume while this is configured, it will look for every index file in this location and if yo change the default file, it will reconfigure any site you have enabled :confused:

Thanks for your help Irv.

---

