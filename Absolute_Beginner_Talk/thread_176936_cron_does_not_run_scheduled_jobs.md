---
title: "cron does not run scheduled jobs"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by p.n on 2006-05-15
I have a back script in my cron.daily directory but this is not run.  i have to run it mannually.  I have also tried crontab but this to refuses to run my script.  ls on the cron.daily directory shows the following:

```
-rwxr-xr-x  1 root root 1555 2005-04-01 16:27 backup_script

```

and my crontab entry looks like this


```
20 59   * * *   root    /etc/cron.daily/backup_script

```

Any ideas?

p.n

---

### Post by patrick295767 on 2006-05-15
I would recommand you to use : 
/etc/crontab
  
1/ First step: 
```
sudo bash
apt-get -f -y install kcrontab gedit
kcrontab
```
  Make what you need !
  
2/ then
gedit /etc/crontab &
  
3/ check in this file you have **root **written in your line
(kcrontab forget it sometimes)
  
4/ In case of problem, post your /etc/crontab 
(PM me, I'll check it if it's not working)
also you should post the result of : > ls -l /etc/crontab
  
Greetings
  
Patrick

---

### Post by p.n on 2006-05-16
Patrick, thanks for the tips bit maybe I did not make it clear enough.  I did in fact also use /etc/crontab (see second code snip in my first post).  The fact that the actual script is in /etc/cron.daily was merely cause I did not bother to move it when testing crontab.

Anyway, still no joy.

Regards
p.n

---

