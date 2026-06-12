---
title: "Corrupt mysql user.myd"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by mrsticks on 2007-03-25
I upgraded my last slackware box today.  Its been 6 years, but a failed hard drive was cause for an upgrade anyways.  ( It's not you, it's me, we're just 2 different people now ).  This was only a small webserver, so I was able to save the info, including the mysql files ( wasnt able to get a proper mysqldump. )

So I installed Edgy server.  But I think I screwed the pooch and messed up my new install's user.MYD file.  I made a copy of that before I edited it, but to no avail.

When I try to start the server:
```
 * Starting MySQL database server mysqld                                                                    [ ok ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```

So I figured I could just blow away the mysql isntall with apt-get remove, or possibly apt-get --purge remove, but I dont think I am using those commands correctly.  I want to completely remove mysql from the system.  Including everything in /var/lib/mysql.

Any help with "uncorrupting" my user.MYD file, or completely nuking mysql, so I can start over, would be greatly appreciated.

Thanks

-peter

---

### Post by Arby on 2007-03-26
Other people are observing the same error as you, although for entirely different reasons. Based on this thread [http://www.ubuntuforums.org/showthread.php?t=112505&highlight=%27Access+denied+for+user+%27debian-sys-maint%27%40%27localhost%27+%28using+password%3A+YES%29%27](http://www.ubuntuforums.org/showthread.php?t=112505&highlight=%27Access+denied+for+user+%27debian-sys-maint%27%40%27localhost%27+%28using+password%3A+YES%29%27) it looks like you might not need to remove mysql at all, just repair the debian-sys-maint account. This thread also claims to have fixed the same issue [http://www.ubuntuforums.org/showthread.php?t=391142&highlight=%27Access+denied+for+user+%27debian-sys-maint%27%40%27localhost%27+%28using+password%3A+YES%29%27](http://www.ubuntuforums.org/showthread.php?t=391142&highlight=%27Access+denied+for+user+%27debian-sys-maint%27%40%27localhost%27+%28using+password%3A+YES%29%27) Maybe you can find something there to help you out.

Arby

---

