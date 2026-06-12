---
title: "proftpd logging"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2006-12-14
In my proftpd.conf file there is no mention of logging but in another user's post he had a copy of his proftpd.conf file and there were the following entries:

```
# It's better for debugging purposes to create log files
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

```

Can I just add those entries in to my proftpd.conf file?

Thanks.

Johnny

---

