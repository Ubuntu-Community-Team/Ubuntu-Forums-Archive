---
title: "Apache Install w/Errors"
date: 2007-06-10
forum: Apple PPC Users
---

### Post by -fred- on 2007-06-10
I'm trying to install apache on a fresh install of Fiesty Fawn. (sudo apt-get install apache)

these are the errors that are returned:
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)

any help would be appreciated.  thanks

---

### Post by -fred- on 2007-06-10
i got rid of that error by installing apache2.  i installed mysql and phpmyadmin.  
i have /var/www/phpmyadmin/config   setup what seems to be correctly.

the new problem is when that i go to install phpmyadmin/scripts/setup.php   when i do that, i get the "Open With/Save To Disk" window.  I did install php5

still looking to get this (mysql,php,rubyonrails,phpmyadmin) up and running so i can develop locally.

thanks in advace

---

