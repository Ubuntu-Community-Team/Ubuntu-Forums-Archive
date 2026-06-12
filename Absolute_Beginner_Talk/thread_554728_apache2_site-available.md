---
title: "apache2 site-available"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by bradleyd on 2007-09-19
hello everyone,

I cant seem to figure this one out. I can get it to work under RH. I have apache2 installed ubuntu 6.10. I have a website in /var/www/wiki.
I am trying add wiki into VirtualHost. Right now /sites-enabled is using the default which is the directory listing of /var/www. I add wiki to site-available.
> <VirtualHost *>
    ServerName wiki.mydomain.com
    ServerAlias  wiki.mydomain.com
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/wiki
    <Directory /var/www/wiki>
        # pcw No directory listsings
        # Options Indexes FollowSymLinks MultiViews
        Options -Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

</VirtualHost>

when I try to visit page [http://wiki.mydomain.com](http://wiki.mydomain.com), it comes up with not found. > The requested URL /wiki/index.php was not found on serevr
When I look in apache2/error.log, it says :
> [error] [client 10.10.100.107] File does not exist: /var/www/wiki/wiki

Somewhere it is adding to the extra wiki on the end of it? I am stumped. I know I can uncomment  Redirect in default(sites-available) and point it to wiki directory and that works, but I would like to get it to work this way.
Thanks in advance,
Brad

---

### Post by bradleyd on 2007-09-19
I got it to work by changing wiki to :
> #FILE: /etc/apache2/sites-available/wiki

NameVirtualHost wiki.mydomain.com:80

<VirtualHost wiki.mydomain.com:80>
#ServerAdmin [email]me@mydomain.com[/email]
ServerName wiki.mydomain.com
ServerPath /wiki
DocumentRoot /var/www/wiki
<Directory>
Options FollowSymLinks
AllowOverride None
Order allow,deny
Allow from all
</Directory>

</VirtualHost>

I then disabled default by:
```
sudo a2dissite default
```
Restarted apache2 and it woks.

---

