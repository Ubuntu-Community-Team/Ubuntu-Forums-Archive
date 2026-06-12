---
title: "Apache2 not working"
date: 2011-12-31
forum: Any Other OS
---

### Post by createdcreature on 2011-12-31
Guys, I know this is not the best place to ask this, but I have recently transitioned to openSUSE, and have installed Apache2 on it using Yast. When I type ```
http://localhost
``` in my browser, it says 

```
Access forbidden!

You don't have permission to access the requested directory. There is either no index document or the directory is read-protected.

If you think this is a server error, please contact the webmaster.

Error 403

localhost
Sat Dec 31 15:54:06 2011
Apache/2.2.21 (Linux/SUSE)
```

Before you ask, all permissions are set at 777.

---

### Post by Dangertux on 2011-12-31
Well you're reaching the server. Is there an index? Also if there is. Is documentroot pointing to the right directory?

Hope this helps.

---

### Post by createdcreature on 2011-12-31
There is an index.htm. I have tried saving the files in

```
/srv/www
```

and

```
/var/www
```

, with no luck.

---

### Post by Dangertux on 2011-12-31
Okay so according to your httpd.conf where is your webroot?

---

### Post by createdcreature on 2011-12-31
What is my webroot?

---

### Post by Dangertux on 2011-12-31
In your /etc/httpd/httpd.conf file DocumentRoot should be defined as something. What is it defined as? That is web root and where your index file needs to be.

---

