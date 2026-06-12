---
title: "how to start a service at booting the system"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by oct03 on 2006-10-08
hi @ll,

I'm an absolute beginner :) please help.

I 've installed XAMPP from apachefriends.org. The installation was successfull and now I'd like to make it run automatically by booting the system, but I don't known how :( . At this time I have to start it in a terminal window as root (su and so)

/opt/lampp/lampp start

Now, please show me how to make.

Many thanks in advandce.

Regards
oct03

---

### Post by Arevos on 2006-10-08
If /opt/lampp/lampp is a service (i.e. it has start and stop commands), then you can link it to a /etc/rcN.d directory.

Ubuntu uses init.d (at least until Dapper), and this works by having different runlevels. The runlevels are organised as follows:

0 (halt the system)
1 (single-user mode, similar to safe-mode in windows)
2 through 5 (various multi-user modes, normal operation)
6 (reboot the system)

The init.d system starts services beginning with an S, and stops services beginning with a K. It deals with the services in alphanumeric order. For this reason, you'll find services that look like "K11cron" and "K01gdm" (GDM will be stopped before Cron because it has a lower number).

You'll want to link a start script to runlevel 2, which Ubuntu uses by default when starting up, and a stop script to runlevels 6 and 0. e.g:

```
ln -s /opt/lampp/lampp /etc/rc0.d/K20lampp
ln -s /opt/lampp/lampp /etc/rc6.d/K20lampp
ln -s /opt/lampp/lampp /etc/rc2.d/S20lampp
```

---

### Post by oct03 on 2006-10-08
wow .. so easy ... it works great 

thank you very much \\:D/

---

