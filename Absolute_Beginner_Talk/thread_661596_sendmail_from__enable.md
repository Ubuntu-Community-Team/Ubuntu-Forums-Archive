---
title: "sendmail_from  enable"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by mattjriley on 2008-01-08
Hi all, 

I need to enable sendmail_from.   PHP info screen: "sendmail_from	= no value"     

i have no idea of how to enable it.

help very welcome.

---

### Post by blueridgedog on 2008-01-08
You can edit your php.ini file (mine is at /etc/php5/apache2/php.ini), yours may be in a different location based on your apache version.

```
gksudo gedit /etc/php5/apache2/php.ini
```

Worked for me.

---

