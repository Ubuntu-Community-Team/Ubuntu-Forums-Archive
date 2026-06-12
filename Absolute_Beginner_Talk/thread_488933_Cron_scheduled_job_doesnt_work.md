---
title: "Cron scheduled job doesnt work"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by 6kwar on 2007-06-30
Hi

I am trying to run sarab.sh file to create a backup using kdar. everything is configured and works like I want it to manually . But when I am trying to setup a cron job to run the file automatically it fails. 
This is how I create my cron job

```
sudo crontab -e 
```

I write
05 03 * * * /usr/local/sarab/sarab.sh

It should run every day at 03:05am

I tried this command.

```
crobtab -u root -e
``` 
but it gave me the same line that I edit later.

I also tried without the sudo and -u root but it just doesn't work.

why and how can I fix it. and maybe it fails from some unknown reason is there a log file?
sarab.sh run only with root privileges. So maybe I need to write it in a special way?  
thanks

---

### Post by GeeZor on 2007-06-30
Have you tried this:

```
 
su -

crontab -e 


```
Now add the line 05 03 * * * /usr/local/sarab/sarab.sh
every user has its own crontab but i am not realy sure this was wat you where looking for.

---

### Post by greg_g on 2007-06-30
Well, from my experience, it is usually best to just do "crontab -e" without the sudo.  I believe (correct me if I'm wrong) but using sudo makes the job be run by root, not you, which could be bad.

So, do "crontab -e" and then put in that line.

One thing to check is to make sure the .sh file has execution permissions set on it.  A easy GUI way to do that is to find it in Nautilus and right click - Properties.  There is a Permissions tab, and should be a check box for "executable." EDIT: it is labeled as "Execute" and "Allow executing file as program"

See if that helps.


greg


Could someone else clarify the sudo vs no sudo for crontab?

---

### Post by GeeZor on 2007-06-30
greg,

every user has his own crontab file...
sudo crontab -e just means you are about to edit the root crontab.. which is not a bad thing.. you might want to schedule a periodic updatedb for instance.. 
and in this case, running the scripts as root is exactly what 6kwar wants. 

And you are right about the permissions. those need to be cheked aswell..

---

### Post by greg_g on 2007-06-30
Thanks GeeZor, I missed the part where 6kwar said the script needed to be run with sudo privileges.

---

