---
title: "Restart PHP5 from Terminal?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-04-26
The title says it all. How do you restart PHP5 from the Terminal?

---

### Post by az on 2007-04-26
Php just is.  It runs when you run a php script.

Do you mean restart apache or mysql?

sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart

---

### Post by Cypher on 2007-04-26
PHP is executed by the webserver when it gets a request for a .PHP/3/4/5 file. So if you've made any changes to the php.ini or something, restart Apache and the changes should take effect.

---

