---
title: "Lamp/Apache install problem"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by adinsenmeyer on 2007-04-04
Hi guys.
I installed ubuntu Desktop without problems. I want to setup my install Lamp server. I have done this before but not on Ubuntu. I was a Fedora Core user and decided to switch to ubuntu and I tell you, it looks better and easier to user that FC6.. anyway
My problem: when doing a sudo apt-get install apache2 in a termina windows, it installed Apache in the var/www/Apache2-default folder. ?? So i google sudo, look at the man pages and I can't find anything about specifying the destination directory. I would like to have apache2 installed under /var/www. Can anyone help me with this ?

Thanks

---

### Post by Bachstelze on 2007-04-04
There's just a little something you need to edit in the Apache config file to have it look in /var/www but I don't remember exactly what it is since I did it a while ago and I just switched my own webserver from Ubuntu to FBSD :p

---

### Post by az on 2007-04-04
The default is to have one site runing once you install apache2.  It is named "default".

You can edit the /etc/apache2/sites-enabled/default file and change the DocumentRoot to point to wherever you like.  By default, it uses /var/www/apache2-default.

Then reload apache2

sudo /etc/init.d/apache2 restart

---

