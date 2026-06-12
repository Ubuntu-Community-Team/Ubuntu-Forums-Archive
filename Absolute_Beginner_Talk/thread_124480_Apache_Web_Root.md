---
title: "Apache Web Root"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Dennis Pedrie on 2006-02-01
Hello,

I've had experience with Apache on Windows, but today is the first time I've installed it on Linux.

I can't find where it setup the Web Root. As in, when I enter [http://localhost/](http://localhost/), where are those documents stored?

Thanks,

Dennis.

---

### Post by Randomskk on 2006-02-01
Try /var/www, I think that's the default.
Look at /etc/httpd.conf or /etc/httpd/conf/httpd.conf (no idea where Ubuntu puts it) for the config file, it may say where it is there.

---

### Post by Dennis Pedrie on 2006-02-01
Yup, that's it. Thank you. :)

---

### Post by DonQuixote on 2006-02-01
I believe you will find the settings in a file called (if you are running Apache2) default in the /etc/apache2/sites-available/ folder.

HTH

John

---

