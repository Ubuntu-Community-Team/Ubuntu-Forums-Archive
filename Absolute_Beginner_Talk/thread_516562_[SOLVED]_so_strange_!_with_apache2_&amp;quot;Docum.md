---
title: "[SOLVED] so strange ! with apache2 &amp;quot;DocumentRoot&amp;quot;"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by iblicf on 2007-08-03
i have  just installed the LAMP , seems no problem  ... so i type "http://localhost " within firefox ,   ... 
```
Not Found

The requested URL  was not found on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu2 Server at localhost Port 80

```

check my [COLOR="Blue"]/etc/apache2/sites-available/default [/COLOR]
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot [COLOR="Red"]/var/www[/COLOR]
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory [COLOR="Red"]/var/www/[/COLOR]>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```

but there do have a index.php( single line phpinfo ) file in /var/www ! and  775 chmod

i check  the log find below: [COLOR="Blue"] /var/log/apache2/error.log [/COLOR]
```
[Fri Aug 03 22:05:52 2007] [error] [client 127.0.0.1] File does not exist: /htdocs
```

i try to "sudo mkdir /htdocs" ,and cp the index.php from /var/www ,, it works ( phpinfo        
)

...anybody can tell me why ? and how to rework it ? was it a BUG? : ) 
```
uname -r
2.6.22-8-generic
```

---

### Post by bernied on 2007-08-03
What have you got in /etc/apache2/sites-enabled ?

---

### Post by iblicf on 2007-08-03
> **bernied said:**
> What have you got in /etc/apache2/sites-enabled ?

that's an empty folder ...

---

### Post by atomkarinca on 2007-08-03
you can try this:

```
cd /etc/apache2/sites-enabled
sudo ln -s /etc/apache2/sites-available/default localhost
```

---

### Post by tehkain on 2007-08-03
I have the same issue on gutsy. Strange.

---

### Post by az on 2007-08-03
> **iblicf said:**
> that's an empty folder ...

Well, that's your problem right there!

sudo a2ensite default

The site needs to be enabled.  It is by default.  You must have dissabled it or deleted the link (same thing)

---

### Post by az on 2007-08-03
> **atomkarinca said:**
> you can try this:

```
cd /etc/apache2/sites-enabled
sudo ln -s /etc/apache2/sites-available/default localhost
```

The file name of the configuration file for the site is irrelevant.

---

### Post by iblicf on 2007-08-03
> **az said:**
> Well, that's your problem right there!

sudo a2ensite default

The site needs to be enabled.  It is by default.  You must have dissabled it or deleted the link (same thing)

well done !  very appreciate ^^

---

