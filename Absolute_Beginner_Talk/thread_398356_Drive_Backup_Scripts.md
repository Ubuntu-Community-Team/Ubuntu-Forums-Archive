---
title: "Drive Backup Scripts"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by pjmckeown on 2007-03-31
Okay, next question. Getting closer to having my system complete.

I have 1 drive called /Photos
I have another called /Photos_Backup

What I want is a script that will do an exact differential copy of every file and folder on Photos to Photos_Backup and I would like to know how to schedule that script to go off every day/night at a given time. 

I assume I could do a dd and put it in a cron job or something, but I am really not sure how to do a cron job. I am sure I could figure out a little shell script to do the backup, just not sure how to schedule stuff yet.

Regards,

Patrick

---

### Post by Skrynesaver on 2007-04-01
```
 crontab -e 
```
will open your cron table for editing in your prefered editor.
If you want something to happen daily at for example 3am
you would enter
```

* 3 * * * /home/pjmckeown/bin/backup.sh

```

Hope that helps

---

### Post by pjmckeown on 2007-04-01
Much appreciated!

---

