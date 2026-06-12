---
title: "simple help with apache.."
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-05
I have a simple apache Q. I am trying to map my webroot directory from /var/www to ~/www... and used the following directive in /etc/apache2/conf.d 
```

Alias /var/www  /home/name/www/ 
<Directory /home/name/www/>
  Options Indexes FollowSymLinks
  AllowOverride All
  Order allow,deny
  Allow from all
</Directory> 
```I restarted apache and it worked perfectly yesterday and today. Now I just made some changes in my php.ini file so I had to restart apache, and it is taking my web browser to /var/www... why is that and how can it be corrected?

---

### Post by sardion on 2006-12-05
Are you certain that what you posted worked?

Try changing the Alias line
to be just

Alias /



The Alias you give is an alias on the web server side so / would be the webroot

---

### Post by habtish on 2006-12-05
> **sardion said:**
> Are you certain that what you posted worked?

Try changing the Alias line
to be just

Alias /



The Alias you give is an alias on the web server side so / would be the webroot


Fisrt off.. that is what I thought it should be and made the alias /, which hadn't worked.. and changed it to /var/www and I am sure it was working... Now I changed it back to Alias /  /home/name/www
Here's what I got...
```

/etc/apache2/conf.d$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   [Tue Dec 05 17:08:18 2006] [warn] The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

---

### Post by tocleora on 2006-12-05
Can you not just change DocumentRoot to that path instead of using an alias?   Do that in /etc/apache2/sites-available/default file.

---

### Post by tocleora on 2006-12-05
Oh and the <directory> info shouldn't go in conf.d, it should also be in /etc/apache2/sites-available/default or I think you might can put it directly in /etc/apache2/apache2.conf...

---

### Post by tocleora on 2006-12-05
sorry for the triple post but also, I believe that Alias is used for url's too.  You would use an alias to make [http://servername.com/foldername](http://servername.com/foldername) point to /this/local/folder like so:

Alias /foldername /this/local/folder

It's not used to point a local folder to a local folder.

---

