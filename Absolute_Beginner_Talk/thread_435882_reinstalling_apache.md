---
title: "reinstalling apache"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by zolw on 2007-05-07
I messed up with my apache and phpmyadmin. How to completly remove (all conf file, everything) apache, phpmyadmin, sql and php5? After then I want to install them all over again, make them to create new default config files etc. how to do that? (using 'apt-ger remove' left conf files on disk).

---

### Post by Bachstelze on 2007-05-07
Use the --purge option to apt-get, for example

```
sudo apt-get --purge remove apache2
```

You can also remove the config files manuallr with *rm*.

---

### Post by zolw on 2007-05-07
worked awesome. thx for tip.

---

