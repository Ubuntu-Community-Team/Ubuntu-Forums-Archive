---
title: "Server name"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by alainsamoun on 2006-07-31
I have the Apache2 server address as:
[http://localhost/~alain/](http://localhost/~alain/)
To make my PHP scripts in Ubuntu compatible with the ones I copied from my windows setup, I'd like to replace the '~alain' by 'php5' is that possible?

---

### Post by Paerez on 2006-07-31
you could do it with a symbolic link. So go into your webroot and make a link called php5 that points to the contents of the alain folder.

If you need more help than that, please post the location of the php5 folder and the alain folder.

---

### Post by alainsamoun on 2006-07-31
Paerez:
If I look at the Apache userdir in the userdir.conf it is: 
UserDir public_html
I have: home/alain/public_html
Sorry I never heard what is 'symbolic link' and I'm not sure of what you call 'webroot'#-o

---

### Post by Paerez on 2006-07-31
your webroot is probably in /var/www/localhost
look in there. If you browse to:
[http://localhost/](http://localhost/)
it will open the "webroot" (the root of your web pages) which is what is in /var.

Try creating an index.html in the /var/www/whatever directory, and in other subdirectories of /var/www to find out where the webroot is.

So, make /var/www/localhost/index.html, browse to [http://localhost/](http://localhost/) and see if it shows up. Then tell me the name of the directory.

---

### Post by alainsamoun on 2006-07-31
I renamed the public_html so I guess the webroot is:
[http://localhost/apache2-default/](http://localhost/apache2-default/)

---

### Post by Paerez on 2006-07-31
ok go to the directory that contains the apache2-default folder, and type:
```
sudo ln -sf /home/alain/public_html php5
```
then browse to:
[http://localhost/php5](http://localhost/php5)

---

### Post by alainsamoun on 2006-07-31
OK! That worked :) 
Thanks!

---

### Post by Paerez on 2006-07-31
sweet!

It basically made a shortcut from /php5/ to ~alain.

---

