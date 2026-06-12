---
title: "Problem with phpMyAdmin in Xampp + Ubuntu"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-10-22
I downloaded and installed Xampp on my Ubuntu 7.04 successfully. Everything in Xampp is functional, except for the phpmyadmin.

When i visit this url -> [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

I get this following error:

> Existing configuration file (./config.inc.php) is not readable.

I thought it was some kind of file ownership problem, so i did this in terminal:

> sudo chown latheesan:latheesan /opt -R

This did not help at all :( can someone help me figure out how to get phpMyAdmin working please :confused:

---

### Post by bolbit on 2007-10-22
try 
```

chmod o+r ./config.inc.php

```

---

