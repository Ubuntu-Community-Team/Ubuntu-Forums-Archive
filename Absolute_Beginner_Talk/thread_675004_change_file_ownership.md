---
title: "change file ownership"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by BiggoCharley on 2008-01-22
Is there a way to change ownership of all files in a directoryin one fell swoop rather than doing each one at a time. My website files are in /var/www/httpdocs.  In order to get apache to serve the web I need to change all users and groups from root to www-data so they agree with the config file.  I started to do this manually, one file at a time but for large directories, found it way too tedious.  I tried chown with a wild card but that didn't work for me.  I'm using apache 1.3.34.  Any suggestions will be apprecoiated.

---

### Post by p_quarles on 2008-01-22
```
sudo chown -R www-data:www-data /var/www/httpdocs/
```
should do the trick.

---

### Post by PeterJS on 2008-01-22
Try:
```

chown www-data /var/www/httpdocs -R

```
The capital R is for recursive so it will change the ownership of the directory and everything under it.

---

### Post by philinux on 2008-01-22
From memory its

sudo chown username -R your directory

---

### Post by emarkd on 2008-01-22
The wildcard should work.  You can also use the -R switch for recursive (travel down all directories as well)

like this:

chown -R user:group *

where user and group are the user and group you want the files to belong to

---

### Post by ptn107 on 2008-01-22
```
sudo chown -R user:group /var/www/httpdocs
```

Replace *user* and *group* as desired.  The -R switch makes it recursive. (Use *man chown* for other useful tidbits.)

---

### Post by philinux on 2008-01-22
This should help for future reference.

[http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)

---

### Post by BiggoCharley on 2008-01-22
I can't thank you all enough -- worked like a charm on the first try. I can't believe the short time it took to get the replies.  This group is great!!!
Charley

---

