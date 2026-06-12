---
title: "help with cron job"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by frozndevl on 2006-12-29
I am trying to setup a script to run every hour. I have written the script and tested it, and it works fine when I manually fire it off. However, I have input it using crontab -e with the following syntax

10 * * * * /bin/bash /home/blank/foldftp.bat

It never seems to fire off. I have also dropped the script into the /etc/cron.hourly directory but it is also not working. I have a feeling that cron is not enabled but I am unable to figure out how to check that. And the script is a modified batch file from my winXP box so I didn't bother to change the name.

---

### Post by mcmanus on 2007-01-01
I am experiencing the same issue: brand new 6.06.1 server box that won't run my crontab.  I have:

```
$ crontab -l
# m h  dom mon dow   command
0,15,30,45 * * * * /usr/bin/fetchmail
```

I can run the fetchmail command manually and it works, but it seems like the cron isn't being fired off at all.  Any ideas?

---

### Post by frozndevl on 2007-01-02
Having played with it a bit more, I have noticed the following items:

1) If I put my command into the /etc/crontab file the script fires off properly.
2) If I review the /var/log/syslog I can see my personal crontab script being called, but it is not apparently executing.

---

### Post by bukwirm on 2007-01-02
type "ps aux | grep cron" - if this returns 
```
$ ps aux | grep cron
root      4266  0.0  0.1   2116   840 ?        Ss   Jan01   0:00 /usr/sbin/cron
alex     11054  0.0  0.1   2876   792 pts/1    R+   00:35   0:00 grep cron

```, (or somethng like it) cron should be running.

---

### Post by mcmanus on 2007-01-03
Yeah, I have a cron daemon running.  This is strange...  it definitely doesn't work for ldap users, and it definitely works for system users.

(also, make sure you have newlines after the line in your cron...  it's listed as a bug in the manpage)

---

