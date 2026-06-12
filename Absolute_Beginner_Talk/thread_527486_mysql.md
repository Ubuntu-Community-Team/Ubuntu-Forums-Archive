---
title: "mysql"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by jakebur01 on 2007-08-16
i created a little php file. When i try to connect to mysql i get
```

Fatal error: Call to undefined function mysql_connect() in /var/www/index.php on line 11
```
Is their something I need to set in my php.ini to turn on a mysql connection. I'm on php5, just installed.

---

### Post by hyper_ch on 2007-08-16
I tend to think you have not all necessary stuff installed.

have a look here at the bottom:  [http://www.howtoforge.com/perfect_setup_ubuntu704_p4](http://www.howtoforge.com/perfect_setup_ubuntu704_p4)

and here: [http://www.howtoforge.com/perfect_setup_ubuntu704_p6](http://www.howtoforge.com/perfect_setup_ubuntu704_p6)

---

### Post by proalan on 2007-08-16
check the old phpinfo

```
echo phpinfo()
```

it should tell you what modules are loaded just look to see if mysql is on the list and enabled.

---

