---
title: "how do I install phpmyamdmin?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-22
I have just installed AMP from the synaptic package manager (Apache, MySQL.php) - how can I install phpmyadmin?

Where is the htdocs folder where I can save the files?

---

### Post by az on 2008-01-22
The default site is apache2-default and it's document root is in /var/www/apaqche2-default.

Install phpmyadmin by running:

sudo apt-get install phpmyadmin

---

### Post by kevinatkins on 2008-01-22
Hi,

From memory, if you use Synaptic to install PHPMyadmin, it should set it up correctly for you. You can test by going to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

If that doesn't work, you'll need to issue a

sudo dpkg-reconfigure phpmyadmin

That will set up Apache so that it looks in the correct place, by aliasing the /phpmyadmin directory of the document root to /usr/share/phpmyadmin

For info, the Apache document root is /var/www

---

