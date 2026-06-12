---
title: "apache2 syntax error"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by spacegypsy on 2007-03-03
Helo,

I 'm trying to figure out why [egroupware won't work]("http://www.ubuntuforums.org/showthread.php?t=373644").

When typing [http://localhost/egroupware/](http://localhost/egroupware/) in my browser I get no connetion.

So I checked if apache2 was running.

When running apache2 in terminal I get this error;

>  * Starting apache 2.0 web server... Syntax error on line 19 of /etc/apache2/conf.d/egroupware:
Invalid command 'php_flag', perhaps mis-spelled or defined by a module not included in the server configuration
                                                                         [fail]


And here is content of /etc/apache2/conf.d/egroupware 

> # Apache and PHP configuration for eGroupWare
#
# Read /usr/share/doc/egroupware-core/phpgwapi/php-configuration.txt and
# /etc/php4/apache/php.ini about the meanings and suggested values for
# the configuration settings.  Many settings are required to have a
# certain value for eGroupWare to function reasonably, so only change
# something if you are sure.

Alias /egroupware /usr/share/egroupware

<Directory /usr/share/egroupware/>
  Options FollowSymLinks ExecCGI
  AllowOverride None
  Order allow,deny
  Allow from all
  DirectoryIndex index.html index.php
  AddHandler cgi-script .cgi
  AddDefaultCharset Off
  php_flag file_uploads on
  php_flag log_errors on
  php_flag magic_quotes_gpc on
  php_flag magic_quotes_runtime off
  php_flag register_globals off
  php_flag short_open_tag on
  php_flag track_vars on
  php_value error_reporting 'E_ALL & ~E_NOTICE'
  php_value max_execution_time 90
  php_value mbstring.func_overload 7
  php_value memory_limit 24M
  php_value session.gc_maxlifetime 1440
  php_value session.save_path /var/lib/egroupware/sessions
  php_value include_path .
  php_value open_basedir /usr/share/egroupware:/var/lib/egroupware:/tmp
  php_value upload_max_filesize 6M
</Directory>

<Directory /usr/share/egroupware/fudforum/>
  AllowOverride Limit Options
</Directory>

<Directory /usr/share/egroupware/phpsysinfo/>
  php_value open_basedir /
</Directory>

What's the problem with line 19 ( php_flag file_uploads on)?

:confused:

---

### Post by justifier on 2007-03-03
do you have all the apache PHP libraries installed?

---

### Post by spacegypsy on 2007-03-03
Probably not!

But I don't know which one is missing.

---

### Post by justifier on 2007-03-03
looks okay to me, try putting a # infront of the error line and run the command again, tell us what happens

---

### Post by spacegypsy on 2007-03-03
I put a # infront of line 19;

> # Apache and PHP configuration for eGroupWare
#
# Read /usr/share/doc/egroupware-core/phpgwapi/php-configuration.txt and
# /etc/php4/apache/php.ini about the meanings and suggested values for
# the configuration settings.  Many settings are required to have a
# certain value for eGroupWare to function reasonably, so only change
# something if you are sure.

Alias /egroupware /usr/share/egroupware

<Directory /usr/share/egroupware/>
  Options FollowSymLinks ExecCGI
  AllowOverride None
  Order allow,deny
  Allow from all
  DirectoryIndex index.html index.php
  AddHandler cgi-script .cgi
  AddDefaultCharset Off
  #php_flag file_uploads on
  php_flag log_errors on
  php_flag magic_quotes_gpc on
  php_flag magic_quotes_runtime off
  php_flag register_globals off
  php_flag short_open_tag on
  php_flag track_vars on
  php_value error_reporting 'E_ALL & ~E_NOTICE'
  php_value max_execution_time 90
  php_value mbstring.func_overload 7
  php_value memory_limit 24M
  php_value session.gc_maxlifetime 1440
  php_value session.save_path /var/lib/egroupware/sessions
  php_value include_path .
  php_value open_basedir /usr/share/egroupware:/var/lib/egroupware:/tmp
  php_value upload_max_filesize 6M
</Directory>

<Directory /usr/share/egroupware/fudforum/>
  AllowOverride Limit Options
</Directory>

<Directory /usr/share/egroupware/phpsysinfo/>
  php_value open_basedir /
</Directory>


then ran "sudu apache2" and got;
> Syntax error on line 20 of /etc/apache2/conf.d/egroupware:
Invalid command 'php_flag', perhaps mis-spelled or defined by a module not included in the server configuration


same error but not on line 19 anymore but on line 20

---

### Post by annda on 2007-03-03
do you have php in
/etc/apache2/mods-available

---

### Post by spacegypsy on 2007-03-03
content of /etc/apache2/mods-available ;

/etc/apache2/mods-available/actions.load
/etc/apache2/mods-available/asis.load
/etc/apache2/mods-available/auth_anon.load
/etc/apache2/mods-available/auth_dbm.load
/etc/apache2/mods-available/auth_digest.load
/etc/apache2/mods-available/auth_ldap.load
/etc/apache2/mods-available/auth_mysql.load
/etc/apache2/mods-available/auth_pgsql.load
/etc/apache2/mods-available/cache.load
/etc/apache2/mods-available/cern_meta.load
/etc/apache2/mods-available/cgi.load
/etc/apache2/mods-available/cgid.conf
/etc/apache2/mods-available/cgid.load
/etc/apache2/mods-available/dav.load
/etc/apache2/mods-available/dav_fs.conf
/etc/apache2/mods-available/dav_fs.load
/etc/apache2/mods-available/deflate.load
/etc/apache2/mods-available/disk_cache.load
/etc/apache2/mods-available/expires.load
/etc/apache2/mods-available/ext_filter.load
/etc/apache2/mods-available/file_cache.load
/etc/apache2/mods-available/headers.load
/etc/apache2/mods-available/imap.load
/etc/apache2/mods-available/include.load
/etc/apache2/mods-available/info.load
/etc/apache2/mods-available/ldap.load
/etc/apache2/mods-available/mem_cache.load
/etc/apache2/mods-available/mime_magic.conf
/etc/apache2/mods-available/mime_magic.load
/etc/apache2/mods-available/modxslt.load
/etc/apache2/mods-available/php4.conf
/etc/apache2/mods-available/php4.load
/etc/apache2/mods-available/proxy.conf
/etc/apache2/mods-available/proxy.load
/etc/apache2/mods-available/proxy_connect.load
/etc/apache2/mods-available/proxy_ftp.load
/etc/apache2/mods-available/proxy_http.load
/etc/apache2/mods-available/rewrite.load
/etc/apache2/mods-available/speling.load
/etc/apache2/mods-available/ssl.conf
/etc/apache2/mods-available/ssl.load
/etc/apache2/mods-available/suexec.load
/etc/apache2/mods-available/suphp.conf
/etc/apache2/mods-available/suphp.load
/etc/apache2/mods-available/unique_id.load
/etc/apache2/mods-available/userdir.conf
/etc/apache2/mods-available/userdir.load
/etc/apache2/mods-available/usertrack.load
/etc/apache2/mods-available/vhost_alias.load

---

### Post by annda on 2007-03-03
i almost give up. apache2 seems to have php_mod enabled. have you tested php on localhost at all? if not, temporarily move egroupware.conf out of conf.d directory and run restart apache.

put a dummy php document in your document root (/var/www) and see if you get any errors when accessing it under localhost/dummy.php

dummy.php
```
<?php

phpinfo();

?>
```

---

### Post by spacegypsy on 2007-03-03
you have to know that I'm a nood in these things.

the odd part is that 3 days ago it worked (i got till making a db in egroupware) then uninstall the all thing tried phpgroupware uninstalled this one too (both completely) and then reinstalled egroupware with synaptic package manager.

and then it began...

now i got :

> Not Found
The requested URL /egroupware/ was not found on this server.

Apache/1.3.34 Server at localhost Port 80

when i type [http://localhost/egroupware/](http://localhost/egroupware/)

what do you mean with?

> have you tested php on localhost at all

anyway thx for helping

this forum rules

---

### Post by spacegypsy on 2007-03-03
I suppose that I have to undo the modication of line 19 before I conitue?

---

### Post by annda on 2007-03-03
ok, i'm confused.

in your previous thread i saw that apache2 runs when you invoke localhost.here all the configuration files are for apache2 as well.

from you last post i can see that you are running apache (1.3.34) not apache2.

could it be that you are running one version of the server and trying to configure another?

if you can do that, remove all egroupware, apache, apache2 and php stuff in synaptic. then delete any leftover directories and config files. you can find them by executing this in the terminal:

```
sudo updatedb
locate apache
```

install apache2 and php5 (recommended by egroupware). install egroupware. if you get any more errors then, post a new thread.

good luck!

---

### Post by spacegypsy on 2007-03-03
Just one last question:

Why is it when I want to install egroupware with synaptic it removes php5 and libapache2-mod-php5?

thx

---

### Post by annda on 2007-03-03
if that is the case, trust synaptic. maybe it has an earlier version of egroupware that works best with php4 or it just has all the dependencies set for php4. (that is the geat thing about synaptic etc. or the debian way of packaging in general - it understands a lot more about dependencies than most of us). go for it - get php4.

---

### Post by spacegypsy on 2007-03-03
Thanks a lot annda!

your're advice did the trick

\\:D/ \\:D/

---

### Post by BadSquishy on 2007-05-23
Hello All -

I found this thread while looking to fix the same problem.  The first thread I found on this problem was spacegypsy's original thread:

[Subject: egroupware installation screen won't show in browser]("http://ubuntuforums.org/showthread.php?t=373644")

I've detailed how I created this problem in that thread.  But now I've found this thread and I've tried a couple of the suggestions.  After I had installed eGroupWare and purged eGroupWare a couple of times I realized something was getting left behind, not getting purged properly, so I tried annda's suggestion of ```
sudo updatedb
locate apache
```
and found quite a number of configuration files.  I deleted a number of files that seemed safe to delete and attempted to install eGroupWare again.  This time I got a different error, but an error none the less (I'm at a different computer now so I can't paste in the error text).  I decided that the real problem was this: When I install eGroupWare it installs 89 packages in all.  When I purge eGroupWare it only purges the one eGroupWare package and just removes the other 88 packages.  What I really needed to do was purge all of the packages, so I fired up gedit and I copied and pasted the list of packages from my terminal into gedit.  In gedit I removed all of the newlines so the list of 89 packages was all on one line, then I jumped back onto my terminal and typed in 

sudo aptitude purge 

and pasted in the 89 packages so everyting was on one line and hit enter.  It purged out all of the configuration files for all 89 packages.  As soon as it was done I installed eGroupWare again
```
sudo aptitude install egroupware
```
and voila, it asked me for the header admin username and password during install (the thing that screwed me up in the first place), and when installation was finished I pointed my browser to my test server and it works!  

So the real problem came from aptitude.  Some may call this a feature, but when a package is automatically installed and then automatically removed it leaves all of the configuration files on the system.  I'd definitely call this a bug myself because subsequent installs of the same software actually failed due to these configuration files being left behind.  Also, if I want to try out new software I'll be installing and purging applications, but all of the config files for the dependencies will be left behind, cluttering up my system. 

Hope this helps anyone who runs into the same problem.  

Regards,

---

### Post by smalldog on 2007-08-26
> **BadSquishy said:**
> Hello All -

I found this thread while looking to fix the same problem.  The first thread I found on this problem was spacegypsy's original thread:

[Subject: egroupware installation screen won't show in browser]("http://ubuntuforums.org/showthread.php?t=373644")

I've detailed how I created this problem in that thread.  But now I've found this thread and I've tried a couple of the suggestions.  After I had installed eGroupWare and purged eGroupWare a couple of times I realized something was getting left behind, not getting purged properly, so I tried annda's suggestion of ```
sudo updatedb
locate apache
```
and found quite a number of configuration files.  I deleted a number of files that seemed safe to delete and attempted to install eGroupWare again.  This time I got a different error, but an error none the less (I'm at a different computer now so I can't paste in the error text).  I decided that the real problem was this: When I install eGroupWare it installs 89 packages in all.  When I purge eGroupWare it only purges the one eGroupWare package and just removes the other 88 packages.  What I really needed to do was purge all of the packages, so I fired up gedit and I copied and pasted the list of packages from my terminal into gedit.  In gedit I removed all of the newlines so the list of 89 packages was all on one line, then I jumped back onto my terminal and typed in 

sudo aptitude purge 

and pasted in the 89 packages so everyting was on one line and hit enter.  It purged out all of the configuration files for all 89 packages.  As soon as it was done I installed eGroupWare again
```
sudo aptitude install egroupware
```
and voila, it asked me for the header admin username and password during install (the thing that screwed me up in the first place), and when installation was finished I pointed my browser to my test server and it works!  

So the real problem came from aptitude.  Some may call this a feature, but when a package is automatically installed and then automatically removed it leaves all of the configuration files on the system.  I'd definitely call this a bug myself because subsequent installs of the same software actually failed due to these configuration files being left behind.  Also, if I want to try out new software I'll be installing and purging applications, but all of the config files for the dependencies will be left behind, cluttering up my system. 

Hope this helps anyone who runs into the same problem.  

Regards,

The problem is caused by the apache2 not load the php4 module automatically. You can using command as:
sudo a2enmod php4
It is not related to aptitude or egroupware, therefore it is not need purge and install the egroupware package.
Good luck

---

