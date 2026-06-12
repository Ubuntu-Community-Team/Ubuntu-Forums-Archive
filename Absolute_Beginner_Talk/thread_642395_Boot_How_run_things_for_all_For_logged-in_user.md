---
title: "Boot: How run things for all? For logged-in user?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-12-16
In what file do you put commands and/or script names  

a. that will have run during boot even if no one logs in
b. that will run for all people who log in
c. that will run only for the specific person who logs in?

Also, is it possible to put in commands in a, b, or c that need sudo to complete, but don't want it to stop and ask for root pwd?

---

### Post by nowshining on 2007-12-16
crontab

[http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/](http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/)

---

### Post by movrshakr on 2007-12-17
I don't think crontab will run things during boot process or "at login time" will it?

---

### Post by nowshining on 2007-12-17
crontab already does :) as it starts up at boot and can start up at other certain times..

---

### Post by movrshakr on 2007-12-17
I am sorry, nowshining, but for me to understand, you are going to have to give me more than these one-liners. It may be obvious to you, but unfortunately it is not to me.

 Exactly how would I use crontab to have things...

a. that will have run during boot even if no one logs in?
b. that will run for all people (every person) who logs in?
c. that will run only for the specific person who logs in?

(each case)

---

### Post by nowshining on 2007-12-17
i was waiting for someone else to come chime in actually hopefully with more info. as i don't use crontab myself and i disabled it from bootup..

open up a terminal and type man crontab and hit enter 

apps -- accessories -- terminal

to exit out of the man page (manual page) press q on ur keyboard

---

### Post by movrshakr on 2007-12-20
I must be dense (a distinct possibility) but I don't see how crontab will run something one single time during the boot up (NOT LOGIN) process.

Note the ONE time, not every minute, hour, day, etc, which seems to be what crontab does.

---

### Post by movrshakr on 2008-04-20
I am again interested in a definitive answer to the original question...which I restate as how to configure so that a program/script: 

a. will run during boot even if no one logs in?
b. will run for all people (every person) who logs in?
c. will run only for the specific person who logs in?

crontab was suggested, but my understanding is that crontab is for things to run repetitively, not just one time at boot--or is that wrong?

---

### Post by joshrobinson on 2008-04-20
> **movrshakr said:**
> I am again interested in a definitive answer to the original question...which I restate as how to configure so that a program/script: 

a. will run during boot even if no one logs in?
b. will run for all people (every person) who logs in?
c. will run only for the specific person who logs in?

crontab was suggested, but my understanding is that crontab is for things to run repetitively, not just one time at boot--or is that wrong?

could you give examples please?

A. are you trying to run a script at boot? load a module?
B. are you trying to start a graphical application at gnomes start?
c. same as b

---

### Post by movrshakr on 2008-04-20
> **joshrobinson said:**
> could you give examples please?

A. are you trying to run a script at boot? load a module?
B. are you trying to start a graphical application at gnomes start?
c. same as b

Well now it is a general "learning" question, so I don't have a specific example.  When I first posted it, I wanted to run a script that copied syslog over into a shared directory so I could see it from another machine on the network.  But I don't need that anymore...I just want to know how to run once, something of my own choosing, that does not normally run automatically for the times/conditions specified.

To make it clearer, let's assume 

a. I have written a script DOTHISONCE that I want to run at boot even if no one logs on.  How?

b. I have written a script DOTHISONCE that I want to run at the time anyone logs on.  How?

c. I have written a script DOTHISONCE that I want to run at the time USERJOE logs on.  How?

---

### Post by joshrobinson on 2008-04-20
> **movrshakr said:**
> Well now it is a general "learning" question, so I don't have a specific example.  When I first posted it, I wanted to run a script that copied syslog over into a shared directory so I could see it from another machine on the network.  But I don't need that anymore...I just want to know how to run once, something of my own choosing, that does not normally run automatically for the times/conditions specified.

To make it clearer, let's assume 

a. I have written a script DOTHISONCE that I want to run at boot even if no one logs on.  How?

b. I have written a script DOTHISONCE that I want to run at the time anyone logs on.  How?

c. I have written a script DOTHISONCE that I want to run at the time USERJOE logs on.  How?

first make your script, save it to your desktop, have it named say scriptname
you want to put it in the /etc/init.d directory, and set it to be executable
```
sudo chmod +x scriptname
```
now you wan to let ubuntu know the scripts there to set it up
```
sudo update-rc.d scriptname defaults
```

now when you startup the computer scriptname will run during the boot processes

as for running a script as when users login, you would use 
system > preferences > sessions, and add the scripts you want to start
now im not sure if this is per user, or for the entire system, i only use one user account so i cant test it

but add a program to start, login as a different user, and see if that application starts for all users or just the one, if its something you want on both, add the application/script to both users sessions

---

### Post by movrshakr on 2008-04-20
Thanks, That's a big help.  

It is a bit more of a process than I expected though.  I thought there would be a file/script somewhere that always runs (for each of the conditions I said) and that you would just put a line in that script to execute the script you want to run.

---

### Post by artesvida on 2008-04-23
You don't need to use update-rc.d to set the script to run at boot.  You can use @reboot with cron instead of specifying the day, month, time settings.

```
man 5 crontab 

...
       Instead of the first five fields, one  of  eight special strings  may appear:

              string         meaning
              ------         -------
              @reboot        Run once, at startup.
              @yearly        Run once a year, "0 0 1 1 *".
              @annually      (same as @yearly)
              @monthly       Run once a month, "0 0 1 * *".
              @weekly        Run once a week, "0 0 * * 0".
              @daily         Run once a day, "0 0 * * *".
              @midnight      (same as @daily)
              @hourly        Run once an hour, "0 * * * *".
...
```

---

### Post by movrshakr on 2008-04-23
Wow, thanks artesvida.  The cron approach was mentioned before, but I was thinking it was for repeated, timed things.  I was unaware of the @reboot possibility, and no one before you chimed in to straighten me out.  So, I think cron would be the easiest way to do it.  Thanks again.

Now, just for academic discussion, are there files, into which we could insert our own commands/scripts, one that runs once at reboot, one that runs whenever anyone logs on, and file(s) that runs uniquely at each user's logon?

---

### Post by artesvida on 2008-04-23
I could be wrong, but I don't know of a single place for all of those things.

A.  one that runs once at reboot
For this you can use update-rc.d or crontab with @reboot

B.  one that runs whenever anyone logs on
Use /etc/profile

C.  and file(s) that runs uniquely at each user's logon
Use /home/<username>/.profile or .bash_profile or .bash_login

If there's a single place to set all of this up, I'm interested in hearing about it too!

---

### Post by movrshakr on 2008-04-23
I didn't state it clearly--was not looking for a single place that would handle all the cases...recognized it would be a different location for each one.

Your answer covered it well.

So there is not a system profile or .profile-like file that is run at boot before anyone logs in?

---

