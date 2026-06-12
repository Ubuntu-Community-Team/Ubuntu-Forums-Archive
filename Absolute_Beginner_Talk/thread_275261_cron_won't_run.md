---
title: "cron won't run"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-10-11
I can't get cron to run...

I'm running rsync to mirror some data between computers and want to automate it with cron.

Here's my crontab:

# m h  dom mon dow   command
 0 *   *   *   *    /home/rsync/cron_test >> /home/rsync/logfile 2>&1


This is meant to run the command /home/rsync/cron_test on the hour every hour.

I stuck the ">> /home/rsync/logfile 2>&1" bit at the end to see what the output of cron would be.

When I crontab -l it shows up ok.
When I run the command manually it works fine.
But cron is refusing to run the command and no output is written to logfile.

Any ideas as to where I'm going wrong?

TIA

BH-T

---

### Post by Bubba Ho-Tep on 2006-10-11
forgot to say - 

I'm using ssh with public/private keys instead of a passphrase

and I don't have a /etc/cron.allow or /etc/cron.deny


so it's neither of those things

---

### Post by mcrae on 2006-10-11
try to play the m h d parameters... for it didn't work with 0 * * * * in the beginning

this is a line from my crontab
```
25 3    * * *   valyo   /usr/local/bin/sychr_01
```

---

### Post by Bubba Ho-Tep on 2006-10-11
Yup that worked, thanks! Putting a number in the hour field instead of * made cron do its thing.

My next question is why? According to the man pages and google searches I should be able to put * wildcards in any of the fields.

---

