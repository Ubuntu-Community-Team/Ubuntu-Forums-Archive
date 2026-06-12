---
title: "seting up apache"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by lupgop on 2008-01-05
I seem to have some old docs; 
i was expecting to fing my apache httpd.conf file under 
/usl/local/apache2/
however it seems now it's in
/etc/apache2/ not sure how i changed ? and the config file is
apache2.conf rather than httpd.conf
anyway all i'm looking to do is set up the documentroot ??
cant find this anymore either ? what is called now ?
so just the directory where apache points for the index.html or alt

---

### Post by nitro_n2o on 2008-01-05
if your documents were in /usr/local you must have installed apache manually from source. Now there are in /etc/ because you've installed apache from apt 

The document root configurations is found in /etc/apahce2/apache2.conf 

or you can just create httpd.conf and it'll work the same. The default installation from apt will put  your documents in /var/www 

hope that helps

---

### Post by dabang on 2008-01-05
If you installed the default Ubuntu package, you can change document root in
/etc/apache2/sites-available/default

Change

```
DocumentRoot /var/www/
```

and

```
<Directory /var/www/>
```

as you like.

---

### Post by lupgop on 2008-01-06
thanks - found that now - still cant see where i change it to point somewhere else ??
i have /var/www/apache2-default
that directory has an index.html file which says "it works"
where do i change the setting in apache2.conf so it point to the directory with my index.htlm file + rest of pages ???

*please ignore - got it now* thanks very much.

---

