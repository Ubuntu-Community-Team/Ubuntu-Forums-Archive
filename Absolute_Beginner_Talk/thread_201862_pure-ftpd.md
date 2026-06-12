---
title: "pure-ftpd"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-06-22
I want to change the options of pure-ftpd when it begins. I want to add -E option to not to allow anonymous people to conect to the server. How can I do it?

---

### Post by optimaco on 2006-07-26
Just create a file in /etc/pure-ftpd/conf:
NoAnonymous
with one line 'yes' (without the quotes)
Then restart the server: /etc/init.d/pure-ftpd restart

Configuration is all explained in the wrapper script (/usr/sbin/pure-ftpd-wrapper):
man pure-ftpd-wrapper

---

### Post by Compact on 2006-09-07
Is there any way to change the welcome message of pure-ftp?

---

### Post by dewcansam on 2008-02-11
I have the "NoAnonymous" file with the boolean value of 'yes' and restarted the server but anonymous access is still allowed. And as a anonymous user i am allowed to post files !!!!!

Is there any clue as to what i am doing wrong ?

---

### Post by dewcansam on 2008-02-11
RESOLEVED 

from = [http://download.pureftpd.org/pub/pure-ftpd/doc/README](http://download.pureftpd.org/pub/pure-ftpd/doc/README)
> With previous command lines, the server will run in the default
configuration. Anonymous FTP logins will be allowed if there's a system
account called 'ftp' and every user of your system will be able to access
the FTP server using his regular login/password pair.


using this info i checked /etc/passwd
sure enough there was a ftp user
so i commented this out
```

$sudo vi /etc/passwd

ftp:x:.....
## became
## ftp:x:.....

$sudo /etc/init.d/pure-ftpd restart

```

and presto no anonymous access anymore 

:guitar:

---

