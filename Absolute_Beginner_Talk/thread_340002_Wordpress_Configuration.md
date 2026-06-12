---
title: "Wordpress Configuration"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Akebono on 2007-01-16
I am trying to run the configuration for Wordpress to create a database in mysql:

sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n UserName localhost

I get the following error:

/usr/share/doc/wordpress/examples/setup-mysql: 38: Syntax error: Bad substitution

I can't seem to figure out what is wrong.

---

### Post by wscheer on 2007-01-19
Akebono,
Looks like its a problem with edgy

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress) if you do a ctrl+f and search for "setup-mysql: 38: Syntax error: Bad substitution" you'll see it at the bottom of the page.

"To correct this, you first need to remove any configuration that may have already been created:
```
rm /etc/wordpress/config-localhost.php
```

Then run the same command but using bash instead of sh:
```
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n (your mysql user) localhost
```"

hope that helps

---

