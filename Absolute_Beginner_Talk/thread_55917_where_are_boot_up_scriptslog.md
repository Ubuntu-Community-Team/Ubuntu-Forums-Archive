---
title: "where are boot up scripts/log"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by Lambert on 2005-08-10
When the system boots it shows scripts/verbose of what's happening during boot up. Are these kept in a log so they can be viewed later? If so where at? Specifically any errors if they are kept separately

---

### Post by fng on 2005-08-11
All logs are kept in /var/log

For boot-up problems you should check /var/log/messages and /var/log/syslog.

---

