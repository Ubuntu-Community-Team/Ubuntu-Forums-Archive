---
title: "phpmyadmin problem"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by rollerbald on 2006-03-22
Hello all, I'm a newbie to Linux (potential Windows convert) and am trying to get phpmyadmin working.  I'll try to make a long story short – I successfully installed Ubuntu, MySql, and ODBC and got everything working OK.  I even had phpmyadmin working but then I decided to uninstall MySQL 4.0 and try to install MySQL 5.0.  Big mistake – could not get things working.  I then decided to deinstall MySQL 5.0, Apache and phpmyadmin and start over.  So far go good.

At this point I have MySQL 4.0, and Apache2 re-installed and seemingly working OK.  Learning from previous threads in this forum I have been able to de-install phpmyadmin and re-install it.  However, whenever I enter 'http://localhost/phpmyadmin/' into Firefox I get the following:

You have chosen to open

Which is a: PHTML file
from: [http://localhost](http://localhost)
What should FireFox do with this file?

Previous threads have suggested that I install libapache2.mod-php5 but when I do that with Synaptic it de-installs phpmyadmin, and whenever phpmyadmin is reinstalled it deletes libapache2-mod-php5 and installs libapache2-mod-php4.

I have tried adding these lines to httpd.conf
AddType application/x-httpd-php .php 
AddType application/x-httpd-php-source .phps 

Still no go – phpmyadmin will not start.

Help would be much appreciated - thanks!

---

### Post by l.tambiah on 2006-03-22
I suggest removing everything neccessary, 

Use the following guide at [https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28php%29]("https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28php%29")

Setup your obdc (i've never done it)

Install Phpmyadmin by typing into terminal:-

$ [B]sudo apt-get install phpmyadmin

[/B]I use the LAMP set up on my breezy box, and phpmyadmin works fine.

---

### Post by rollerbald on 2006-03-22
Problem solved.

I used Synaptic to install php5, php5-mysql, php5-cgi.

Works OK now.

---

### Post by indytim on 2006-03-22
Glad you got everything working.  Just to share recent experience from my recent build of LAMP. I just went to the phpMyAdmin site and downloaded the latest stable release of phpMyAdmin.  Inserted it into it's own folder beneath the root, did the usual configuration thinger and it's up and working well.

Just thought I'd share that way of doing it as an alternative to the method mentioned above.

IndyTim

---

### Post by Brennan on 2006-08-21
I'm having the same problem as far as clicking on a .php file and I'll get a Firefox popup message if I'd like to save the .php file to disk or "open with".  I am using PHP5, MySQL, Apache 2 and I already have a php-based website on an Intranet which works just fine.  I'm scratching my head trying to figure things out, and I know the answer is probably a simple one, but does anyone have any idea as to what I'm overlooking?

I went to my /var/www/phpmyadmin/scripts directory and clicked on setup.php and it's doing the same thing.  I even removed and re-installed PHPMyAdmin as well, all to no avail.

Any and all help will be greatly appreciated.

---

