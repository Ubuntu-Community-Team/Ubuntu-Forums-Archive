---
title: "Crontab"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-12-11
The following code excecutes rrd_hddtemp.pl every 1 min


```
*/1 * * * * root /usr/local/bin/rrd_hddtemp.pl > /dev/null
```


Can i modify it to run every 1 sec?

---

### Post by geek_Man on 2006-12-11
If you did (and I don't know if you can) I think that would *really* slow down your computer.

---

### Post by lamego on 2006-12-11
You can create a script which is called by cron to run 60 times your script with a sleep 1 between them.
Using crontab you can't setup tasks with the seconds detail.

Usually such frequent tasks run from a endless loop or service not from crontab...

---

### Post by meniscus on 2006-12-12
thanks. ill try that.

---

