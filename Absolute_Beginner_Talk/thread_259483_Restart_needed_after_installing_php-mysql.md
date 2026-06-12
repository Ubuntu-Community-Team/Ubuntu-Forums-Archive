---
title: "Restart needed after installing php-mysql?"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by locoHost on 2006-09-17
I got my LAMP setup going pretty good. My PHP page tried to connect to MySQL and failed because the function mysql_connect was not found. I didn't have php-mysql installed. I installed it but the page still has the same error. Must I do some kind of restart to get it going?

Thanks guys :-)

---

### Post by kidders on 2006-09-17
You may have to restart apache, so its php.ini is reparsed.

---

### Post by lamego on 2006-09-17
```
sudo /etc/init.d/apache2 restart
```

---

