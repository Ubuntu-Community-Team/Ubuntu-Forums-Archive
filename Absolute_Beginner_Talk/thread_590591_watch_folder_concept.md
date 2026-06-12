---
title: "watch folder concept"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-10-24
Hi, 

Id like to monitor my upload directory (say via a cron process every x minutes) and perfom certain events when a new file is recieved. ie ftp the file somewhere else and then delete it.

(how) is this possible?

cheers

c.

---

### Post by nick_h on 2007-10-25
Yes, use find with cron.  For example use something like:
```
find /dir -type f -mmin -5 -exec script '{}' \;
```
-type f finds files
-mmin -5 find files modified in the last 5 mins
then you can use the -exec to execute a script or other command where {} is the file found.

See:
```
man find
```
for more information.

---

### Post by cnschulz on 2007-10-25
Thank you...

I have just seen how awesomly awesome the find command is... life is great!

:)

c.

---

