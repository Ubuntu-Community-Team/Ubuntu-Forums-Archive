---
title: "I can't get PHP working - I need a LAMP on my 7.10"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by ICEcoffee on 2007-11-12
Hi all. Despite looking at various postings, none have helped. I have been used to working with a 'WAMP' environment on windows XP and want the equivalent on Ubuntu 7.10 desktop, so I can develop web apps.

Following some threads using the command line, I have managed to get Apache2 working, I checked pointing browser to localhost. But cant get PHP to function. PHP test file doesn't run.

because I followed advise using the command line and not the default desktop sofware installer, I don't know where software is loaded AND how to un-install if I needed to start from scratch, and this is all before I install MySQL.

Can anyone point me help with the above PHP issue AND point me to a 7.10 how-to?

Thanks

---

### Post by az on 2007-11-12
In 7.10 run

sudo tasksel install lamp-server

and all the php, mysql and apache packages will be installed for you.

See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by ICEcoffee on 2007-11-12
I did that and nothing happened, no return of info or errors. Is that because MySQL is already installed?

---

