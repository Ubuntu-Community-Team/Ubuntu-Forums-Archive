---
title: "[SOLVED] Unable to install Apache and PHP"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by sajiv_k on 2007-08-12
I'm unable to install Apache and PHP on Ubuntu.

I wrote these commands at the terminal screen

For Apache:

sudo apt-get install apache2

For PHP 

sudo apt-get install php5 libapache2-mod-php5

Both the commands gave me a 'package not found' error message

I'm using desktop edition of 7.04

---

### Post by MenZa on 2007-08-12
"Package not found"? Have you tried updating your package list:

```
sudo apt-get update
```

Also, there is a great tutorial on installing a full LAMP (Linux Apache, MySQL, PHP) solution [here](https://help.ubuntu.com/community/ApacheMySQLPHP).

---

### Post by zvacet on 2007-08-12
**synaptic>edit>mark packages by task>LAMP**

---

### Post by sajiv_k on 2007-08-12
Thanks mates.

It worked :). 

Initially **LAMP** wasn't listed in 

**synaptic>edit>mark packages by task**


But it was there after I ran 

```
sudo apt-get update
```

---

### Post by yangmi0313 on 2007-08-13
yeah, when you meet these problem, It always related to the sources.list.

---

