---
title: "Run Cron Job at Night?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by firefly2442 on 2007-04-23
I know it's possible to setup a cron job to start at a certain time but is it possible to make it stop at a certain time?  For example, I want to run a cron job between 11:00pm and 7:00am every night.

Thanks. :)

---

### Post by Cypher on 2007-04-23
You know in all my years of using Linux, I never bothered much with CRON..but I can take a few (hopefully educated) guesses..

Cron will start a given job at a particular time, I'm not sure if it monitors the amount of time it takes. However, if you wanted to start a job and then make sure that it doesn't run for more than 30 mins, you could create a second job that is 30 mins later and it would be a script that would basically check on the job you care about. If it is still running, you can safely stop/kill it.

Regards

---

### Post by Rinzwind on 2007-04-23
You can always add another cronjob that kills the 1st one.

Let's say you start vlc

> $ ps -ef | grep vlc
rinzwind 10233     1  4 20:25 ?        00:00:00 wxvlc /home/rinzwind/Desktop/[KissSub]_Winter_Cicada_(Fuyu_no_Semi)_OVA1_[19D5EC21].avi


The command killall {process} would do it

So
> killall wxvlc
would nuke all wxvlc instances.

Just use the script you used to start that process to kill it.

---

### Post by Cypher on 2007-04-23
Phew, so I wasn't completely off-base..:D

---

### Post by dannyboy79 on 2007-04-23
what kind of a program? the man pages are a wealth of info

man cron

you could just put something like this within crontab

 00 22 * * * root /usr/bin/bittornado
: 02 22 * * * root /user/bin/stop.sh

and within the stop.sh, you would just put

sudo killall bittnorado

---

### Post by firefly2442 on 2007-04-23
Sweet thanks.  I tested out the commands and it seems to have worked.  I'll see tonight if it will run.  Thanks again! :)

---

### Post by firefly2442 on 2007-04-24
Worked great!  Thanks. :)

---

### Post by dannyboy79 on 2007-04-24
what was the command and will you share for other users? despite you saying that you got it to work, many new users wonder exactly how they format the cron file and what commands work within it. thanks

---

### Post by firefly2442 on 2007-04-24
I used KCron to setup two cron jobs.  One was to run the commandline program "dnetc" every day at 22:00, and the other was to run this script:

> 
#!/bin/bash
killall dnetc


every day at 6:30.

Pretty simple. 

Oh, and make sure the user has permissions in order to run the program and script.  I tried running it as sudo (root) and it didn't work because it required a password.

---

