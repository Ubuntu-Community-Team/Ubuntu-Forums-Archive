---
title: "ssl and the sites-enabled/000-default config file"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-07-03
Hi, I recently installed the 6.06 LAMP server and ssl. I registered with the free server sertificate authority [www.cacert.org](www.cacert.org) as well. I am confused as to how to configure the config files though.  I set up web site directories to: 
/var/www/html/ and /var/www-ssl/html/.  Am I supposed to edit the file 
/etc/apache2/sites-enabled/000-default?  Or is that file some how linked to the /etc/apache2/sites-available/default config file??  If I am suppose to edit it, can some one point me to a how to or describe how?  That would be appreciated.  I  have attempted a few of the different posts I have read regarding this, but have not yet been able to navigate to [https://examplesite.com](https://examplesite.com), only [http://examplesite.com](http://examplesite.com).

Thanks

---

### Post by sickdude on 2006-07-03
did you install the openssl modules?

---

### Post by kpm on 2006-07-03
yes, I installed openssl, all seems fine with it... I just can't seem to find any docs on how to actually configure this apache lamp install of 6.06 with the added bits...

---

