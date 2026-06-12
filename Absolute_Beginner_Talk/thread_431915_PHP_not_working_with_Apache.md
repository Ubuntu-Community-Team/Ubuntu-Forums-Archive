---
title: "PHP not working with Apache"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by chymo on 2007-05-03
I have installed Apache2 and php5 but php is not working.  I do not think it is plugged in to Apache correctly.  Apache was installed first, then php and mysql files installed later... using the lamp ubuntu community guide.  

What can I check to get this running?

---

### Post by scottious on 2007-05-03
Well, I'm not sure if this will help very much because this is what I did on my Gentoo Linux system.

There should be an apache config file somewhere that has this line:

```
APACHE2_OPTS="-D DEFAULT_VHOST"
```

Sometimes, you have to add -D PHP5 inside of the quotes.  However, I have not had to do this for my install of PHP and Apache2 for quite some time so I very well could be wrong.

Also, in your main apache config file (typically httpd.conf) this following line should be present:

```
LoadModule php5_module        modules/libphp5.so
```

Again, this is what I have in my Gentoo installation so it may not be exactly the same.

---

### Post by scottious on 2007-05-03
Also, don't forget to restart Apache.

---

