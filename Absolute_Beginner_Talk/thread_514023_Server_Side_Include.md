---
title: "Server Side Include"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by tungv0 on 2007-07-31
Hi, I'm trying to turn on the server side include in apache2. I have found out that there are 2 ways to do so. The first way is to use mod_include but this one is not recommended. The other way is to use the XBitHack. I have check with my apache by using phpinfo and see that it has not been turned on (its value is 0). I messed around with the apache2.conf and httpd.conf but I can't find XBitHack. Do you know where can i find the XBitHack and turn it on for apache2.

Thanks in advance.

---

### Post by Pragmatist on 2007-07-31
Do any of these help?
[http://ubuntuforums.org/showpost.php?p=936856&postcount=4](http://ubuntuforums.org/showpost.php?p=936856&postcount=4)
[http://ubuntuforums.org/showthread.php?t=101045](http://ubuntuforums.org/showthread.php?t=101045)
[http://ubuntuforums.org/showpost.php?p=115405&postcount=2](http://ubuntuforums.org/showpost.php?p=115405&postcount=2)
[http://httpd.apache.org/docs/2.0/mod/mod_include.html#xbithack](http://httpd.apache.org/docs/2.0/mod/mod_include.html#xbithack)

---

### Post by tungv0 on 2007-10-12
Thanks for this help, even thought I have just looked at it after long time, it helped me a lot but when I try XBitHack on in this directory: <directory /var/www/>XBitHack on </directory> and restart apache, it gives me this error: Invalid command 'XBitHack', perhaps misspelled or defined by a module not included in the server configuration
 failed!
Can someone help please

---

### Post by tungv0 on 2007-10-12
Ok, I have figured out how to fix it. It turned out that I need to a2enmod include and restart apache. Now that error has gone, however I set XBitHack on as indicated above, but when I use phpinfo() to test it on browser, the XBitHack directive is still 0 for both local value and master value. Here is my /etc/apache2/sites-available/default 
> 
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
                XBitHack full
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                XBitHack full
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

</VirtualHost>


---

