---
title: "Server absolutely not working"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by old_newbie on 2006-12-05
I installed a fresh Ubuntu 6.10. Later on I installed all updates etc. My main goal is to have this amchine as a part outside the network to safely develop php on mysql at a apache server.
But... after reading X instructions I still cant get the server to function. Apache2 is installed, so is mysql, I think, but I can't execute any php-files. The machine doesn't know how to handle them. Could it actually be that the apache-installation lack php and that I have to install PHP separately?

Another strange thing is that my pre-defined web directory is in /var/www/apache2-default

Anyone with any idea? :confused:

---

### Post by compwiz18 on 2006-12-05
Did you install the php5 package?  and the php5-mysqli package?  and just delete /var/www/apache2-default, so that your /var/www directory is empty.  Then the default should just be /var/www.

---

### Post by old_newbie on 2006-12-05
I am not sure if I installed any PHP-package at all? I need to use PHP lower than 5, i.e. 4.4.4. Isn't PHP bundled within Apache2? If I have to install PHP separately, do I then need to shut down the Apache server?



Are you saying that I can delete /var/www/apache2-default ? This is the place where the default Apache index(.html) files are. Do I have to reconfigure any Apache-files in order to tell Apache to look somewhere else for the files under Localhost? And which permission do I have to reset this(ese) eventually file(s) to after editing them?:confused:

---

### Post by compwiz18 on 2006-12-05
OK, I'll try and be a little bit clearer - explaining things isn't my greatest strength.

PHP isn't bundled with Apache - it comes in a seperate package, php4.  If you decide to use php5 instead, just install the php5 package.

I believe you can just delete, and it should work.  If it doesn't, tell me.  I don't know off the top of my head where the files are, but I can find them if you need me to.

Hope this helps.

edit: and one other thing: if you wish to edit a file, just use **gksudo gedit /name/of/file** - this way you don't have to mess with the file permissions.

---

### Post by old_newbie on 2006-12-05
Thanks, this clearified a lot! I assumed PHP was bundled with Apache... Also superthnaks for the command-tip, that was really clever!

:D

---

### Post by az on 2006-12-05
See here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

install
apache2 php5-mysql libapache2-mod-php5 mysql-server

and you are good to go.

---

### Post by hyper_ch on 2006-12-05
Here's a step-to-step guide on how to setup everything:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

