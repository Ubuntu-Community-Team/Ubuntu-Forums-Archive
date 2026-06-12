---
title: "apache installed cant find localhost"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-02-21
Hello,

I have just installed Apache2 on Gutsy. Now I enter localhost / 127.0.0.1 / 127.0.1.1 in the URL but it does not find the apache "It works" screen.

I also checked the httpd. conf that is empty.

What to do to get Apache 2 working?

thx,
ben

---

### Post by ben22 on 2008-02-21
sudo /etc/init.d/apache2 restart

produces the following

[B]root@ben-desktop:/home/ben# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                              httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
[/B]

---

### Post by ben22 on 2008-02-21
hmm, 

I changed the ports.conf to

Listen 80, but it isn't working either

Any help out there?

---

### Post by subzero316 on 2008-02-29
see ur apache n all is workin as it displayed when u entered ur localhost addr...it only displayed what is in ur   [COLOR="Red"]/var/www/apache2-default[/COLOR]....put your index file in that

---

### Post by antonr on 2008-03-03
Do this all as root.

Use this to control apache2.

	apache2ctl start|stop|restart

In Apache 2, httpd.conf is deprecated. 
Use /etc/apache2/apache2.conf  instead.

The sites-enabled directory has just one symbolic link in it
which points to a file in sites-available.

	  /etc/apache2/sites-enabled/000-default  -->
	  /etc/apache2/sites-available/default
		VirtualHost
		    DocumentRoot

The sites-available/default file is a config file with DocumentRoot.
Make a copy of the sites-available/default file.

	cd /etc/apache2/sites-available/
	cp default mysite

Remove the existing symbolic link.

	cd /etc/apache2/sites-enabled/
	rm 000-default

Recreate the 000-default link, pointing it at the mysite file we just created.

	ln -s ../sites-available/mysite 000-default

Now modify the new config file.

	nano /etc/apache2/sites-available/mysite

Find the DocumentRoot directory setting and change it to where your website files are.

Edit /etc/apache2/ports.conf to set port 8082 instead of default 80.

	apache2ctl restart

The above changes were enough to get my website working locally.

	konqueror [http://127.0.0.1:8082](http://127.0.0.1:8082)

You should see your index.html file rendered.

---

