---
title: "problem installing Joomla"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by gibbo81 on 2006-09-29
Hi everyone,

I'm trying to install Joomla on Ubuntu 6.06 LTS. I have followed the instructions on [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla) but when I attempt the installation by browsing to [http://localhost/joomla](http://localhost/joomla) I get the error:

Not Found
The requested URL /joomla/joomla_1.0.11-stable-full_package.tar.bz2_files/ was not found on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80

I am guessing it has to do with permissions on the /var/www/joomla directory. I have run sudo chown -R www-data:www-data /var/www/joomla but still cannot browse the directory.

Cheers in advance,

Gibbo

---

### Post by gibbo81 on 2006-09-29
Don't worry guys, I worked out the problem. Seems I had moved the full Joomla_1.0.11-Stable-Full_Package.tar.bz2_FILES directory to /var/www/joomla instead of just the contents.
All is working fine now.
Cheers,
Gibbo

---

