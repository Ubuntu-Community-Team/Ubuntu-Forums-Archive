---
title: "Clean slate?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tipalm73 on 2007-05-15
Hi,

I installed Ubuntu, and attempted to set up a webserver with drupal.

Through trial and error I progressed at a slow pace. Now i'd like to uninstall apache php5 drupal mysql and start over with a clean slate. I planned to just reinstall Ubuntu Server (done this 5 times) BUT I figured I'd ask if there was an easier way to get to square one.

Thanks in advance!

\\:D/

---

### Post by ikonia on 2007-05-15
you can just do apt-get --purgre remove $package-names (eg: mysql-server)

and it will remove everything to do with that package.

---

### Post by tipalm73 on 2007-05-15
Thank you!

---

