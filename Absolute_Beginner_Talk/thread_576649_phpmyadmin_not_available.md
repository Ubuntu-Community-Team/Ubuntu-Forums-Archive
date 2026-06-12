---
title: "phpmyadmin not available?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-10-15
I installed apache, php, phpmyadmin like this..

 sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql


But when i go to localhost/phpmyadmin it is not there ? Apache is running though..
Also can anybody tell me where everything is installed, i could only find the www dir.

---

### Post by mech7 on 2007-10-15
oh i see php does not run either.. can i uninstal by the same command with uninstall ?

---

### Post by Dr Small on 2007-10-15
```
sudo apt-get remove apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql && sudo apt-get autoremove
```

---

### Post by mech7 on 2007-10-15
Oh i rebooted and now php and mysql is running.. not latest version though PHP Version 5.2.3-1ubuntu6

but stil pretty recent :) and mysql is running also.. but where did it put phpmyadmin ? cause that still does not work.

---

### Post by don durito on 2007-10-19
same problem here
i tried to ```
sudo aptitude purge phpmyadmin
``` and did a reinstallation, but still no phpmyadmin. where the heck is it gone. 
if i take a look at /var/www/ there is no phpmyadmin either.
so please help

yours 
don

---

