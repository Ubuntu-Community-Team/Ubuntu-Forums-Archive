---
title: "what is cron.daily trying to mail (and why can't it)?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2008-01-31
I see the following every day in my syslog...
 
```

Jan 31 07:38:15 white syslogd 1.5.0#1ubuntu1: restart.
Jan 31 07:38:15 white anacron[7896]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Jan 31 07:38:15 white anacron[7896]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jan 31 07:38:15 white anacron[7896]: Normal exit (1 job run)

```
 
How do I figure out what it's trying to mail and make it stop?  I don't need sendmail on that computer
 
Thanks

---

### Post by emarkd on 2008-01-31
It's trying to email you it's results.  That's its default behavior.  You can see what crontab is doing every day by running

```
crontab -e  
```

Of course, that's your personal crontab.  You can put a sudo in front of it to see what root's crontab may be doing.

---

