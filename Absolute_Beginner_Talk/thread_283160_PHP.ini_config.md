---
title: "PHP.ini config"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by dboyer02 on 2006-10-23
I did a LAMP install of Ubuntu Server 6.06, added only Xubuntu desktop, did an update on all programs and have been using the [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) guide slowly and carefully.

When trying to configure the php.ini file, my default extension directory  shows as "./" When I do a "locate mysql.so" it returns 2 directories:

/usr/lib/perl5/auto/DBD/mysql/mysql.so (106.8kB) and
/usr/lib/php5/20051025/mysql.so (43.7kB)

I've tried using entering them both, one at a time, into php.ini, saving, then restarting Apache with "sudo /usr/sbin/apache2ctl restart". The only thing I noticed that someome above did differently was to use a different Apache restart command. (etc/init.d/apache2 restart)

Q's:
-Is the mysql.so file supposed to be in two locations?
- Which one is the normal default, "best bet" or known "good" location to use? 

Thanks for your assistance.

---

### Post by po0f on 2006-10-23
dboyer02,

[quote=dboyer02]-Is the mysql.so file supposed to be in two locations?[/quote]

MySQL is a popular RDBMS, so people like to build support for it into their products.  Hence, the files in Perl's and PHP's directories.

[quote=dboyer02]- Which one is the normal default, "best bet" or known "good" location to use?[/quote]

I think your "best bet" would be to use the one located in the PHP directory, since you are setting up php.ini.  ;)

---

