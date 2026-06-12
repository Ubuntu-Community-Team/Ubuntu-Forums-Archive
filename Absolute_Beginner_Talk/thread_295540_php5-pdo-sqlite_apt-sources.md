---
title: "php5-pdo-sqlite apt-sources"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by l09f1l3 on 2006-11-08
Hi,

I am struggling to install SQLite PDO for PHP 5 on ubuntu hoary.  The only sources I find for it are:

deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all

I do an apt-get update
I can find the package when searching for it, but installing does not work, I get the error:

E: Broken Packages.  So, I assume the sources listed above contains invalid packages and finding a better source will help.

Any ideas?

---

### Post by an.echte.trilingue on 2006-11-08
dotdeb is a repository containing debian packages.  Ubuntu is based on debian and also uses the apt package manager, but Ubuntu is not the same thing as debian and you can seriously bugger your system if you try to mix them.

All of these packages are available in ubuntu's native repositories.  Read [this tutorial]("http://www.howtoforge.com/apache2_with_php5_and_php4_p2") and be sure not to get the steps for debian sarge and Ubuntu mixed up.

Good Luck!

-mat

---

### Post by l09f1l3 on 2006-11-09
Thanks, However, this still doesn't help me with sqlite pdo.

after changing my sources.list, and typing sudo apt-cache search php5-sqlite-pdo, I still don't have much joy, no packages found.

](*,)

---

