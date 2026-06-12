---
title: "How to view log errors at Boot  ?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by uncle-c on 2007-08-03
Hi, I've installed Ubuntu 7.04 server edition and am getting mysql errors at bootup. The mysql server service is not starting and I would like to know what is causing the error. I read somewhere that boot logging is no longer available. I have checked the various boot log files and nothing seems to be recorded.
Is there any way of finding the mysql error at bootup time ?

Cheers,
Uncle

---

### Post by dannyboy79 on 2007-08-03
you can view dmesg but I don't think that'll show why mysql failed to load. You can look at syslog.

the best thing to do would be to try to start the mysql server with verbose and debugging options set. 

something like this.

mysqld --log

check this out:
[http://dev.mysql.com/doc/refman/5.1/en/using-log-files.html](http://dev.mysql.com/doc/refman/5.1/en/using-log-files.html)

---

