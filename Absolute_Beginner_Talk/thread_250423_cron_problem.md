---
title: "cron problem"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by wgato on 2006-09-04
I'm having a hard time getting a cronjob to run.
can anyone suggest what i might be doing wrong?

* * * * * /home/tr/perl updateNowPlaying-temp.pl

i've tried editing it with both crontab -e and emacs crontab_file, using and not using single and double quotes, specifying a user, putting the perl script in the users home directory and in /etc/cron.d (always using the full path) and i dont remember what all else.

---

### Post by Jussi Kukkonen on 2006-09-04
> * * * * * /home/tr/perl updateNowPlaying-temp.pl
Do you really have perl intalled in */home/tr/*?
Maybe you meant */usr/bin/perl /home/tr/updateNowPlaying-temp.pl*?

---

### Post by sirlancelot on 2006-09-04
The format for a crontab is like this (separated by spaces):

**[minute] [hour] [day-of-month] [month] [day-of-week] [user] [command]**

From the looks of it, I think your missing the user.

Keep in mind that the way you are setting that up is it will run every minute, so your "now playing" will be delayed by a minute, unless the track happens to change right before an update begins.

---

### Post by Jussi Kukkonen on 2006-09-04
> **sirlancelot said:**
> The format for a crontab is like this (separated by spaces):

**[minute] [hour] [day-of-month] [month] [day-of-week] [user] [command]**

From the looks of it, I think your missing the user.


This is only true for the root crontab, user crontabs do not have "user" field. See *man 5 crontab*.

---

### Post by sirlancelot on 2006-09-04
> **Jussi Kukkonen said:**
> This is only true for the root crontab, user crontabs do not have "user" field. See *man 5 crontab*.Oops :-/ I was looking at the root crontab when I wrote that, didn't bother to look at my user's crontab for differences.

Apologies for mis-information.

---

### Post by wgato on 2006-09-04
yes, Jussi Kukkonen thats it!

thank you everyone, for your help.

---

