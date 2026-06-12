---
title: "Checking Cron jobs work OK"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-11-08
I use kCron as a GUI for crontab.

I'm running a very small number of cron jobs - two are for converting streaming audio into an MP3, the other is a "clean up" job.

Under Feisty these were running OK. Under Gutsy the two audio conversion ones don't seem to kick off OK, though they do if I go for the "Run Now" option in kCron. So the scripts obviously work.

I thought, therefore, it may be an idea to get the output in a text file so I can see what is tripping up.

I therefore have in kCron something along the lines of:

/home/<me>/scripts/script name > /home/<me>/Desktop/job1.txt

I ran the Clean up script manually last night and it duly produced a job1.txt file. This, though, is completely blank. Is that expected behaviour if the job works OK, or do I need to do something else for it to log in detail?!

Thanks!

---

### Post by indytim on 2007-11-08
Just a passing thought.  Have you considered writting out a small text file (log file) at the end of your bash program to see if it's running?

IndyTim

---

### Post by qprfact on 2007-11-08
Sounds a good idea - how would I do that?

---

### Post by qprfact on 2007-11-09
Anyone?!

---

### Post by qpieus on 2007-11-09
Your job1.txt file being empty means there was no standard output from your script, but doesn't mean the script ran error free. Error messages will not go to your file as you currently have your cron job line written. Change your cron job line to this to get standard output AND any error output to your file
```
/home/<me>/scripts/script name > /home/<me>/Desktop/job1.txt 2>&1
```

---

### Post by qprfact on 2007-11-09
That did it! Thanks!

---

