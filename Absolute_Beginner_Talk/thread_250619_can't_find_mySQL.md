---
title: "can't find mySQL"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-09-04
Hey all, how are you doing? I am dabbling in web design and when I went through the package manager it told me that mySQL was already installed, but I can't find it anywhere? Any ideas?

I also downloaded bluefish, very nice so far, I just can't figure out how to get the tags colour-coded. So if anyone knows that one too, it would be great help.

Thanks a lot,
Have a great day,
David the K

---

### Post by Skogix on 2006-09-04
Start it with [sudo /etc/init.d/mysql start] and tab from "mysql" in the terminal.

---

### Post by jimmygoon on 2006-09-04
sudo apt-get install mysql-server mysql-client mysql-common

enjoy!

---

### Post by Uluen on 2006-09-04
What do you mean you can't find it? It's a service running, not a application under the Applications menu.
```
$ /etc/init.d/mysqld status
```

If you're looking for ways to maintain your dbserver I recommend [phpMyAdmin]("http://www.phpmyadmin.net/home_page/index.php").

---

### Post by dckirba on 2006-09-04
> **Uluen said:**
> What do you mean you can't find it? It's a service running, not a application under the Applications menu.
```
$ /etc/init.d/mysqld status
```

If you're looking for ways to maintain your dbserver I recommend [phpMyAdmin]("http://www.phpmyadmin.net/home_page/index.php").

Well, I looked under /etc/init.d and it's not there... so I'll do apt-get and get it. I'm just trying to teach myself here so I'm not really sure how mySQL works or exactly what it does. First forage into this territory :) 

Thanks a lot guys,
David K

---

### Post by Uluen on 2006-09-04
Good luck, MySQL with PHP is a very powerful combo.
See wikipedia for more about [SQL]("http://en.wikipedia.org/wiki/SQL").

---

### Post by dckirba on 2006-09-05
Hey, thanks a lot. I'm very new to this and I'm a bit over my head. Any idea where I can find some really basic info on phpmyadmin? All their documentation assumes some level of experience and I have none.

Thanks,
David K

---

### Post by Uluen on 2006-09-05
phpMyAdmin is pretty straighforward in my opinion but I've used it for years. Maybe you just need to learn some basic SQL?

Here's one [tutorial]("http://www.sql.org/sql-database/sql-tutorial/").
You may find it easier to understand if you use the commandline, that way you don't have to learn the GUI as well.

---

