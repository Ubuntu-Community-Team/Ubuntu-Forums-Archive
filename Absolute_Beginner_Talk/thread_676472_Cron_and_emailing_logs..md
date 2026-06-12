---
title: "Cron and emailing logs."
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by nomad1970 on 2008-01-23
I'd like to have cron email me the output of an rsync backup.

I'm a bit puzzled as to where one configures mail server information, smtp etc.  Do I need to install some type of program to handle smtp?

Also, I don't see any output / log files from the rsync backup, is there an additional line I need to add to the actual dailybackup executable, or to crontab?

ubuntu server 7.10

Thanks!

---

### Post by dcstar on 2008-01-24
> **nomad1970 said:**
> I'd like to have cron email me the output of an rsync backup.

I'm a bit puzzled as to where one configures mail server information, smtp etc.  Do I need to install some type of program to handle smtp?

Also, I don't see any output / log files from the rsync backup, is there an additional line I need to add to the actual dailybackup executable, or to crontab?

ubuntu server 7.10

Thanks!

Install the **postfix** and **mailx** packages to allow you to handle SMTP and also send/test mail via a terminal.

As for the rsync stuff, I don't know.

---

### Post by nomad1970 on 2008-01-27
I'll check those out.

Thanks!

---

