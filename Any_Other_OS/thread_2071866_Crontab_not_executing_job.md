---
title: "Crontab not executing job"
date: 2012-10-16
forum: Any Other OS
---

### Post by rohit verma on 2012-10-16
Hi all,

I am using CentOS release 6.2 (Final).
have file /var/spool/cron/root .
**crontab -l** shows :
PATH=$PATH:/etc
01 * * * * date >> /testCron.tsv

but not getting /testCron.tsv...

Regards,
Rohit.
:popcorn:

---

### Post by cjhabs on 2012-10-16
Try including the full path to the date command

---

### Post by rohit verma on 2012-10-16
hi cjhabs,

tried ur suggestion.. didn't worked..

Regards,
Rohit

---

### Post by cjhabs on 2012-10-16
crontab -l should just show cron entries - the first line, PATH=$PATH:/etc,  is not a cron entry so I suspect that the scheduler is quitting on you. If you remove that first line that should fix the issue

---

### Post by papibe on 2012-10-16
Hi rohit verma.

You are trying to write to the root directory. That would only work if the user who is executing the script has permissions to do that.

If you are creating the crontab with your regular user, that won't work.

Either change the destination to a directory you have permission to write, or create the crontab as root (I would avoid the last option at much as possible).

Let us know how it goes.
Regards.

---

### Post by rohit verma on 2012-10-17
thanks buddies,
for your responses..

now **crontab -l** shows :
* * * * * /bin/date >> /tmp/testCron.tsv

and wooho! its working....

Regards,
Rohit.

---

