---
title: "cron not working"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by wgato on 2006-09-23
i'm having a heck of a time getting cron to work.

i've tried running crontab -e and adding
0 * * * * mine /home/mine/ghostbin/autoftp.exp
* * * * * mine /bin/echo "cron test"

i also sudo root and ran crontab -e and added 
0 * * * * root /home/mine/ghostbin/autoftp.exp
* * * * * root /bin/echo "cron test"

and i tried putting the script in /etc/cron.hourly/ and that doesnt work either. (but like more precise control over when it runs.)

looking over all the cron tutorials, i cant figure why this doesnt work.  anyone have some suggestions?

---

### Post by subzero79 on 2006-09-23
Check is cron daemon is started.

sudo /etc/init.d/cron start

if is already running maybe there is an issue with the script that you are trying to execute. Can you post it here?

---

### Post by wgato on 2006-09-23
i didnt know it had to be started :/

seems thats the problem:
$ sudo /etc/init.d/cron start
Password:
 * Starting periodic command scheduler...                           [fail]

now i've got something new to look into

thank you very much for the help

---

### Post by subzero79 on 2006-09-23
Try stopping and starting it again. or restart it

sudo /etc/init.d/cron stop
then start

or 

sudo /etc/init.d/cron restart

also check the permissions of the script so that is executable.
If the script executes a graphical aplication cron won't start that script for what i understand.

---

### Post by Daniel9389 on 2006-09-23
mayby if you tryed righting it in the teminalor google linux it

---

### Post by wgato on 2006-09-23
> **subzero79 said:**
> Try stopping and starting it again. or restart it

sudo /etc/init.d/cron restart

also check the permissions of the script so that is executable.
If the script executes a graphical aplication cron won't start that script for what i understand.


sudo /etc/init.d/cron restart
worked.

i aded the line in my own crontab -e
* * * * * mine /home/mine/ghostbin/test

with the full text of the file test:
#!/bin/sh
echo "cron test"

i chmod 755 test so the permissions from ls -al test are
-rwxr-xr-x 1 mine mine 28 2006-09-23 22:52 test

what could i be doing wrong?

---

### Post by chrisfay on 2006-09-24
> i aded the line in my own crontab -e
* * * * * mine /home/mine/ghostbin/test

with the full text of the file test:
#!/bin/sh
echo "cron test"

i chmod 755 test so the permissions from ls -al test are
-rwxr-xr-x 1 mine mine 28 2006-09-23 22:52 test

what could i be doing wrong?

How do you know its not being ran by cron? If you don't pipe the output of the script somewhere, you will have to check the logs to see if was ran. Either that, or you can check the mailbox of the bash files owner; cron generally emails cron completeion emails to the owner of the file it runs unless you send it to /dev/null.

Try modifying your script to something like:

```
#!/bin/bash

echo "Cron Test" >> /crontest.txt
```

When the time has passed that you have cron scheduled to run the script, type:

cat /crontest.txt

...and your output "Cron Test" should be in there. That way you know it ran.

Just an idea....

---

### Post by wgato on 2006-09-24
thanks for the suggestion

i had just been checking my mail but i tried piping the output to a file as you advised... nothing

it just seems crons not working

---

### Post by chrisfay on 2006-09-25
The first thing I would do is verify the daemon is actually running:

```
ps aux | grep cron
```

This should spit out one line of output showing that it is indeed running. If you get no output, its not.

If it is, I would then check your syslog in /etc/syslog for entries made by cron doing daily tasks. The cron package is responsible for shecduling a host of things on your computer and will log itself; so check that as well. If no entries, then you can be fairly certain its not running. 

Again, if you do have entries and cron is actually running, but not your scripts, I would do some checking on the way you have your script scheduled to run. Maybe you have not set the scheduling correctly. Try putting the script in /etc/cron.hourly; this will force it to run hourly and will help you decide if its cron or some error on your part. Check your /etc/syslog again. 

Note: I'm not sure when the hourly cron actually runs, I thought it runs on the hour but that is not the case; possibly runs the hour following the time you added the script. Just put your script in that folder and check it later on.

---

### Post by wgato on 2006-09-25
ps aux | grep cron 
says its running (plus i've stopped and started cron several times in the process of working on this)

/etc/syslog.conf has cron commented out

#cron.*           /var/log/cron.log
daemon.*       -/var/log/daemon.log
kern.*            -/var/log/kern.log

i removed the # and will see if i can check the log soon.
the daemon and kern lines have a **-** before the directory.   should i had one to the cron line as well?
 
i do have the script in /etc/cron.hourly, though i will need more specific timing.

---

### Post by chrisfay on 2006-09-25
> /etc/syslog.conf has cron commented out

Cron should log to /etc/syslog regardless...

---

### Post by wgato on 2006-09-25
i maybe confused but 
there is no entry for syslog in /etc

---

### Post by chrisfay on 2006-09-25
> there is no entry for syslog in /etc

```
sudo vi /etc/syslog
```

...will show you the entries. Use the 'Down Arrow' or 'Page Down' key to scroll through them..

---

### Post by wgato on 2006-09-25
it opens a new file

---

### Post by chrisfay on 2006-09-25
> it opens a new file

Sorry, its actually /var/log/syslog....Don't drink and post.;) 

```
sudo vi /var/log/syslog
```

Look for cron entries in there...

---

### Post by subzero79 on 2006-09-25
Install postfix and mutt(terminal mail client) to generate a localhost mailbox to output of the cron jobs. 

try

sudo apt-get install mutt

Cron will ALWAYS output a message to your localhost INBOX unless you specify not to do it.

When you install mutt add this line to the crontab

MAILTO=user@localhost

where user is the name that you configure your mail client

To check the mail output of cron type mutt in the terminal.

Other method try running a cron job with a graphical application like xmms. Search the forum for the line for crontab for doing that.  i can't find it right now.

---

### Post by boban on 2006-10-03
Don't know if you have solved this problem... But I had it the same way...

If you have script in /etc/cron.hourly try running command

```

run-parts --list /etc/cron.hourly

```

It should list all jobs it would normaly run... If your script isn't listed - try changing its name... (that was mine issue - script "test.sh" didn't want to start...)

---

### Post by wgato on 2006-10-04
subzero79 - yup, i've got postfix and mutt installed.  i dont get any mail about it.
xmms is an interesting thought but i dont have a gui.

edit:  it appears postfix is not working.  it was but... thanks for the hint

---

### Post by evilghost on 2006-10-12
> **boban said:**
> Don't know if you have solved this problem... But I had it the same way...

If you have script in /etc/cron.hourly try running command

```

run-parts --list /etc/cron.hourly

```

It should list all jobs it would normaly run... If your script isn't listed - try changing its name... (that was mine issue - script "test.sh" didn't want to start...)

Thank you, good call.  I was searching these forums because I had placed a file *backup.sh* in /etc/cron.daily and it refused to run.  Doing *run-parts --list /etc/cron.daily* didn't show it listed.  Renaming it from *backup.sh* to *backup* fixed it as it now shows up in *run-parts --list /etc/cron.daily*.  Odd that .sh files are "filtered", I've never seen this behavior before.

---

### Post by PilotJLR on 2006-11-17
> **boban said:**
> Don't know if you have solved this problem... But I had it the same way...

If you have script in /etc/cron.hourly try running command

```

run-parts --list /etc/cron.hourly

```

It should list all jobs it would normaly run... If your script isn't listed - try changing its name... (that was mine issue - script "test.sh" didn't want to start...)


Good call! I stumbled across this as well... run-parts doesn't care for the .sh extension, it appears. I don't recall this behavior with Red Hat.

Oh well, now we know not to make cron scripts with a .sh extension!  :rolleyes:

---

### Post by paul.maddox on 2006-12-03
> **boban said:**
> Don't know if you have solved this problem... But I had it the same way...

If you have script in /etc/cron.hourly try running command

```

run-parts --list /etc/cron.hourly

```

It should list all jobs it would normaly run... If your script isn't listed - try changing its name... (that was mine issue - script "test.sh" didn't want to start...)


I cam across this problem too when trying to get something in /etc/cron.daily to run! Thanks very much for solving it for me, the problem was the file in /etc/cron.daily/ had an extension and run-parts didn't like that.

---

