---
title: "Adding a job to cron"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2008-02-02
I am having troubles with mythtv not updating the listings from schedules direct unless done manually. All the settings are correct and I can not figure out why this is occuring. If I run /usr/bin/mythfilldatabase --update from bash then it updates fine. As a workaround, I would like to add this as a cron job to run ever night at 4am. How would I go about doing this? I have never worked with cron before. From what I have briefly looked at, would the steps be to crontab -e in bash, then add the line 0 4 * * * /usr/binmythfilldatabase --update. Is this correct?

---

### Post by doddo on 2008-02-02
> **jba6511 said:**
> I am having troubles with mythtv not updating the listings from schedules direct unless done manually. All the settings are correct and I can not figure out why this is occuring. If I run /usr/bin/mythfilldatabase --update from bash then it updates fine. As a workaround, I would like to add this as a cron job to run ever night at 4am. How would I go about doing this? I have never worked with cron before. From what I have briefly looked at, would the steps be to crontab -e in bash, then add the line 0 4 * * * /usr/binmythfilldatabase --update. Is this correct?

The syntax looks all right for me! Does the cron daemon mail you?

```
mailx 
``` to read messages from crond.

Also what does the logs say?

Could this be a permission issue?

---

### Post by jba6511 on 2008-02-02
thanks, went  through the logs and did not see anything. Other than the default recording directoy, which other folders should I check the permissions on?

---

### Post by doddo on 2008-02-02
Test adding this to your crontab file (its a longshot i thought crond mailed output of preformed programs to the user owning the crontab)

 ```
MAILTO=youruser
```

 I Just figured your user maybe did not have permissions to launch the program, 

You can also do a
```
grep -l /var/log/* 
``` To see which of your logs contains messages for cron. I think /var/log/messages or /var/log/daemons are probable to contain cron stuff

also, this is maybe a bit far fetched, but do u have the cron daemon running?

---

### Post by doddo on 2008-02-05
Come to think of something.

What is the contents of 
```
/etc/cron.deny
```

---

