---
title: "Trying to upgrade from 6.06 to 6.10"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Nigel Hewlett on 2007-09-27
I am trying to upgrade from Dapper Drake to Feisty Fawn so am starting by upgrading from Dapper Drake to Edgy Eft.  I type:

gksu "update-manager -c"

and everything starts off fine.  Then I get an Error window with a message saying it cannot retrieve these:

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found

..... and upgrade does not happen.  Any idea what I should do?

Nigel Hewlett

---

### Post by overdrank on 2007-09-27
> **Nigel Hewlett said:**
> I am trying to upgrade from Dapper Drake to Feisty Fawn so am starting by upgrading from Dapper Drake to Edgy Eft.  I type:

gksu "update-manager -c"

and everything starts off fine.  Then I get an Error window with a message saying it cannot retrieve these:

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found

..... and upgrade does not happen.  Any idea what I should do?

Nigel Hewlett

Hi as I read this morning that is the proper way to update but you could see issues with additional packages. So you might have to edit your apt source and remove any additional repo's. Hope this helps and good luck!

---

### Post by zvacet on 2007-09-27
If I´m not to late,no need to remove repos.Just coment them (put # in front of the line).After your upgrade is finish you need to change sources list from Dapper to Edgy

```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```


After that remove # sign you put before and 

```
sudo aptitude update
```

---

