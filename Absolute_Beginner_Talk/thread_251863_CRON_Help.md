---
title: "CRON Help"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-09-06
How would I go about adding a script I wrote to clean out files and  thumbnails to a cron file.  I would like the script file to run say every hour or 2 while my machine is running. The script file is only 3 lines long, but does what I need.

Please try to make your instructions as easy as possible since I am a new user to ubuntu and linux in general.

Donald

---

### Post by amohanty on 2006-09-06
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)
[http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/using-cron.html](http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/using-cron.html)

try it out. if you run into trouble, post back.

HTH
AM

---

### Post by alienexplorers on 2006-09-06
Thanks for the help.  Now have a place to start and learn more about cron.

Thanks

---

### Post by amo-ej1 on 2006-09-06
I think the best place to look is in the manpages on your system. You could check 
```

man 8 cron
man 1 crontab
man 5 crontab

```
The first for the manpage of the daemon, the second for the manpage of the crontab command used to modify the cronjobs and man 5 crontab for the file syntax used in the previous command. Especially the last document you should read, the first two are almost explaining themselves.

---

