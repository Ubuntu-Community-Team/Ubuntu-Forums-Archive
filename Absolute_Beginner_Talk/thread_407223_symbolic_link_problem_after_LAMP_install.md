---
title: "symbolic link problem after LAMP install"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ghmercado on 2007-04-11
hi my default file (000default) at /etc/apache2/sites-enabled/ says it allows symlinks ie:

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

but when i loaded my index.php at /var/www/ all the symlinks to images (../img/someimage.jpg) don't work.

help me out? everything is still at default after just running apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server. Many thanks.

---

