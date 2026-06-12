---
title: "Changing The ServerName in Apache2"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by KMuchane on 2008-04-10
Hello...,

I am trying to configure Apache2.2 which I installed the other day.
My problem is not that complex...or so I thought.I want to change the ServerName to something more appropriate but apparently I cannot...but first things first. Here are the contents of the /etc/apache2/htttpd.conf which I edited:

NameVirtualHost 127.0.0.1

<VirtualHost 127.0.0.1>
        ServerName [www.kinuthia.com](www.kinuthia.com)
        ServerAlias kinuthia.com
        ServerAdmin [email]webmaster@kinuthia.com[/email]
        DocumentRoot /home/kinuthia/www/

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /home/kinuthia/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>


When I restart the sever through /etc/init.d/apache2 restart, I am helpfully reminded that:
* Restarting web server apache2     
        apache2: apr_sockaddr_info_get() failed for tchane
        apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
        
                                                                                 [ OK ]
        'tchane' is the computer's hostname.

So, every time  I try to access the files in the DocumentRoot I have to type in 127.0.0.1. How do I get round this?
Someone to the rescue?
Thanks!

---

### Post by GreenB on 2008-04-10
Try adding a 
```

ServerName -your_prefered_servername-

```
at the end of the httpd.conf file.
had the same error, but it dissepeared when i added 'localhost'

---

### Post by mbeach on 2008-04-10
not to change the subject, but from what I've read (I'm not an expert) and experienced, it seems that using the /etc/apache2/sites-available folder for your site specific conf files is the way to go instead of using the /etc/apache2/httpd.conf file.

Once you have your config file in the sites-available, you can use the a2ensite command to enable your site.  If you need to take a site down, you can use the a2dissite command.  Some more info at:
[http://www.debian-administration.org/articles/207](http://www.debian-administration.org/articles/207)

Once using the site-available, sites-enabled type structure, it does seem to be very easy to maintain.

---

### Post by KMuchane on 2008-04-10
Guys,

Thanks for your response but I am still stuck.

Firstly,mbeach,I created a configuration file - kinuthia_site - for the website in the /etc/sites-available/ folder and then symlinked it with the command  sudo a2ensite /etc/apache2/sites-available/kinuthia_site to enable it.

That is after I commented the line /etc/apache2/httpd.conf in the main configuration file /etc/apache2/apache2.conf incase they clashed.
But when I use the ServerName given in that file - ie /etc/apache2/sites-available/kinuthia_site -  [www.kinuthia.com](www.kinuthia.com), Firefox says it cannot find the server at [www.kinuthia.com](www.kinuthia.com). To make matters interesting it even has an alias. But when I use 127.0.0.1 everything is fine,fine...

GreenB, I tried adding the ServerName at the end but nothing changed,would you mind being clearer,where did you add 'localhost'?:confused:

Thanks!

---

### Post by GreenB on 2008-04-10
in the end of the httpd.conf file like:
```

ServerName localhost

```
but i gotta mention that i dont intent to use my box to serve pages on the web, but only for building and testing, 
Anyway it solved the later of the two warnings

---

### Post by OffAxis on 2008-04-10
I'm confused;
Are you trying to set up a local server for an intranet (just for your LAN) site or a generally-available open-to-the-public internet site?

---

### Post by GreenB on 2008-04-10
no i am just setting up a php/sql/apache to test out some web designs before uploading

---

### Post by mbeach on 2008-04-26
@KMuchane - I suppose it may be an issue of whether or not this machine is currently responding to requests at [www.kin](www.kin)....

by that I mean is your registrars's or host pointing to this machine, and is your router forwarding to that machine etc... (all depending on your situation).

If you simply need a test locally that its serving up pages you can edit your /etc/hosts file and add a line like 
127.0.0.1   [www.yoursite.com](www.yoursite.com)

then goto [www.yoursite.com](www.yoursite.com) in your browser.  Once its actually 'live' and if its hosted elsewhere you may want to remove that line from your hosts file.
(might want to wait for a second opinion on this approach).

This is how I've done it when the server is on the same side of the firewall as me, and using the full domain name seems to send me off into the mystic.  Its also how I manage to test the various websites all with different domain names from my local machine.  Quick search on Google yeilds:
[http://johnbokma.com/windows/apache-virtual-hosts-xp.html](http://johnbokma.com/windows/apache-virtual-hosts-xp.html)
(about half way down the page) which is mainly for XP, but the ideas for the hosts file for testing of the virtual hosts by name may be what you are running into.

Hope this helps somewhat.
mb.

---

