---
title: "Location of cron log"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by doctor bangali on 2007-05-09
Where are the logs of cron job stored?

---

### Post by h3rt3q on 2007-11-28
yeah.. where is it?

---

### Post by chenel on 2007-12-07
By default cron logs to /var/log/syslog, so to see all recent cron events you could do

```

sudo grep CRON /var/log/syslog

```

---

