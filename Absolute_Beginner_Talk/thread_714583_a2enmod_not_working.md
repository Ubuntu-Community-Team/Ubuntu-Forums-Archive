---
title: "a2enmod not working"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-03
i am trying to do a2enmod php5 like tutorials say however however is say that module in not installed, how do i install it.  searching on google give me pages on php5 and how to use it and i try searching for in the download manager but no luck.

---

### Post by Average Joe on 2008-03-04
a2enmod is a command to enable or disable modules for the apache2 web server. From your post it is not really clear to me whether you have installed apache2 at all.

If so, make sure you have php5 installed as well:
```
sudo aptitude install php5
```
The php5 module should then automatically be enabled in apache. In /etc/apache2.mods-enabled/ you should see both php5.conf and php5.load then. If not, you could indeed try:
```
sudo a2enmod php5
```

In case you do not have an apache webserver installed, there is no point in enabling modules for it and trying to do so will obviously would work then.

---

### Post by RyanZec on 2008-03-04
I have apache2, php5, and libapache2-mod-php5 all installed and still can't enable the php5 mod,

---

