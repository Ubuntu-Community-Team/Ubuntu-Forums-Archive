---
title: "Apache"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by kcirtap on 2007-07-09
I have installed apache and everything seems to work since I can access [http://localhost](http://localhost) without problems. I don't know where the apache www directory is though, any ideas? I found the directory in: /var/www but I don't have any access at all and cannot add my websites there, so i'm starting to wonder if it really is the right place.

---

### Post by black_ice on 2007-07-09
first it depends on how you install it if you install it manually i think you will find it at /usr/share/apache2 

and there you can find all configuration files and you will find httpd.conf there also & you can edit there ur

document root and get you web site working

---

### Post by EndPerform on 2007-07-09
/var/www is the correct place, but by default it's owned by root.  You could change the ownership of /var/www:

```
sudo chown -R username:username /var/www
```

That will allow you to put things in there.  Replace username with your username in both instances.

---

### Post by kcirtap on 2007-07-09
> **black_ice said:**
> first it depends on how you install it if you install it manually i think you will find it at /usr/share/apache2 

and there you can find all configuration files and you will find httpd.conf there also & you can edit there ur

document root and get you web site working

I installed it trough apt-get. I found something in /usr/share/apache2 like you said, but it was just a bunch of icons and other things. In the /var/www directory everything was in place like phpmyadmin and the apache index page that writes "it works". I have no idea how I can add something there if it only complains about it however.

edit:
It worked with the line: sudo chown -R username:username /var/www

Thanks..

---

