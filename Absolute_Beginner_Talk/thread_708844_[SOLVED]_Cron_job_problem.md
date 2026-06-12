---
title: "[SOLVED] Cron job problem"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by jualansandal on 2008-02-26
Hi all, Im beginner in Linux especially Ubuntu.
Right now I am facing problem about cron job.
I have already add new task in the cron (crontab -e) , the command is this :
1 0 * * * /home/hardono/Desktop/Kettle-3.0.1/sh kitchen.sh -file=/home/hardono/Desktop/Kettle-3.0.1/project/UnzipAllJob.kjb -level=Minimal

after that I start the cron job by typing cron start(before that I must kill a task that locking the cron).
But after I waited for a moment, looks like the task is not executed. FYI the task is a Kettle Job(getting zip files from ftp server and uncompress it).

I am looking forward for explanation why the cron is not executing the task , and also the solution if any .

Thanks

---

### Post by jualansandal on 2008-02-26
Anyone ?

---

### Post by HermanAB on 2008-02-26
I think cron is disabled for ordinary user accounts by default.  Read the cron man page for details on how to enable it.

---

### Post by glennric on 2008-02-26
Cron is enabled for ordinary users by default.  The problem is that you are telling cron to run the job at 1 minute after midnight, not every minute.
Try 
```
1 * * * * /home/hardono/Desktop/Kettle-3.0.1/sh kitchen.sh -file=/home/hardono/Desktop/Kettle-3.0.1/project/UnzipAllJob.kjb -level=Minimal
```

For more information on cron check out the following link:
[Newbie: Intro to cron]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html")

---

### Post by jualansandal on 2008-02-26
Thanks.

But, how should I make it runs every minute

---

### Post by northern lights on 2008-02-26
> **HermanAB said:**
> I think cron is disabled for ordinary user accounts by default.  Read the cron man page for details on how to enable it.
I don't think it is. I run cronjobs from Gutsy on my laptop without root privileges (I've just figured out how to launch graphical apps tonight). I might have enabled it somehow and don't remember, but I doubt it.

Anyway, does the shell script run in the first place (i.e. have you tried it)? Also, or if not, paste the entire command, as it is written after the "1 0 * * *" into a terminal and check whether that works.

What does the script execute? If it's a graphical application, try: ```
* * * * * export DISPLAY=:0 && /home/hardono/Desktop/Kettle-3.0.1/sh kitchen.sh -file=/home/hardono/Desktop/Kettle-3.0.1/project/UnzipAllJob.kjb -level=Minimal 
``` (obviously replace some of the *s)

Is your cron daemon running? Try ```
/etc/init.d/cron start
```
You might have to do that as root, not sure. If that fails, try: ```
/etc/init.d/cron restart
```
If either works, try executing a scheduled job again...

---

### Post by Oldsoldier2003 on 2008-02-26
> **jualansandal said:**
> Thanks.

But, how should I make it runs every minute
cron cannot be depended on to reliably run a job every minute. there will be some variation depending on system load and other factors.  but  * * * * * /pathtoyourjob should run "every minute"

---

### Post by glennric on 2008-02-26
> **jualansandal said:**
> Thanks.

But, how should I make it runs every minute

Sorry the line in my last post wasn't quite right.  The following line will make the job run every minute of every hour of every day of the year.

```
* * * * * /home/hardono/Desktop/Kettle-3.0.1/sh kitchen.sh -file=/home/hardono/Desktop/Kettle-3.0.1/project/UnzipAllJob.kjb -level=Minimal
```

---

### Post by glennric on 2008-02-26
By the way if you install the package "gnome-schedule" you can edit the crontab with a gui.

---

### Post by Oldsoldier2003 on 2008-02-26
> **glennric said:**
> By the way if you install the package "gnome-schedule" you can edit the crontab with a gui.

just write your crontab file in any text editor then use crontab -u <username> <crontabfilename> no reason to install another package

---

### Post by northern lights on 2008-02-26
> **jualansandal said:**
> But, how should I make it runs every minute
Thought you wanted it to run then & there, way simpler, duh. What a dunce I am...

* * * * * /home/hardono/Desktop/Kettle-3.0.1/sh kitchen.sh -file=/home/hardono/Desktop/Kettle-3.0.1/project/UnzipAllJob.kjb -level=Minimal[/CODE]

In * * * * * command:
1st*: minutes from 0 to 59
2nd*: hours from 0 to 23
3rd*: days of the month from 0 to 28/29/30/31
4th*: month from 0 to 11
5th*: weekdays from 0 to 6

a * basically means "any value"...

---

### Post by glennric on 2008-02-26
> **Oldsoldier2003 said:**
> just write your crontab file in any text editor then use crontab -u <username> <crontabfilename> no reason to install another package

You don't get it.  For a newbie the gnome-schedule gui is very convenient.  You don't have to learn the format of the crontab.  You don't have to edit a text file.  That is the whole point of a gui.

---

### Post by northern lights on 2008-02-26
> **glennric said:**
> For a newbie the gnome-schedule gui is very convenient.  You don't have to learn the format of the crontab.  You don't have to edit a text file.  That is the whole point of a gui.
Agreed.

---

### Post by glennric on 2008-02-26
By the way "gnome-schedule" is just a front end for crontab.  It does the job of editing the file for you.  If you do want to learn the format of crontab, schedule a job in the gui and then open the crontab file.  For instance if you want to run a job every 15 minutes instead of every minute use
```
*/15 * * * * job
```
gnome-schedule has an option to do this and if you type "crontab -e" after using the gui you will see the line above.

---

### Post by jualansandal on 2008-02-26
I tried * * * * *, but the cron job still not execute the job.
And I also confused with cron restart command, everytime I "cron restart" then I got this message "cron: can't lock /var/run/crond.pid, otherpid may be xxxxx: Resource temporarily unavailable"

thanks all for answering

---

### Post by glennric on 2008-02-26
You should restart cron with the command 
```
sudo /etc/init.d/cron restart
```
Although, why are you trying to restart cron.  Cron should be running as soon as you boot, and you don't need to restart cron every time you make a change to the crontab.

---

### Post by jualansandal on 2008-02-26
O, I see, 
but is there any suggestion for a simple task to test the "every minute" scheduler is working or not ?

---

### Post by northern lights on 2008-02-26
With "* * * * *" it should execute every minute. Alternatively, you could check the current time (X:YY) and try "YY+1 X * * *", but I think that's redundant.

I might repeat myself, but what does the script do? And does it launch a graphical application?

---

### Post by glennric on 2008-02-26
Make a text file called "cron-test"
```
#!/bin/sh
echo "This is a test" >> ~/test-result
```
Then make that file executable with "chmod +x cron-test"
Add the line 
* * * * * ~/cront-test
to your crontab.
After a minute look in your home directory and see if there is a file name "test-result".
If it is there the job ran.  Every minute it should add another line to that file if you read the file.

---

### Post by jualansandal on 2008-02-26
> **northern lights said:**
> With "* * * * *" it should execute every minute. Alternatively, you could check the current time (X:YY) and try "YY+1 X * * *", but I think that's redundant.

I might repeat myself, but what does the script do? And does it launch a graphical application?

The script is a kettle script. Kettle is an Open Source ETL tool. My script itself does the taking zip file from ftp server and unzip it. I already tried the script manuall and it is working well.

---

### Post by jualansandal on 2008-02-26
> **glennric said:**
> Make a text file called "cron-test"
```
#!/bin/sh
echo "This is a test" >> ~/test-result
```
Then make that file executable with "chmod +x cron-test"
Add the line 
* * * * * ~/cront-test
to your crontab.
After a minute look in your home directory and see if there is a file name "test-result".
If it is there the job ran.  Every minute it should add another line to that file if you read the file.

I'll try it, thanks

---

### Post by jualansandal on 2008-02-26
The test is successful, now I am more confused

---

### Post by glennric on 2008-02-26
The test succeeded?  You mean the job ran as expected?  So what is the confusion?

---

### Post by northern lights on 2008-02-26
So it is a graphical app! Then try:> **northern lights said:**
> ```
* * * * * export DISPLAY=:0 && /home/hardono/Desktop/Kettle-3.0.1/sh kitchen.sh -file=/home/hardono/Desktop/Kettle-3.0.1/project/UnzipAllJob.kjb -level=Minimal 
```
(basically, add "export DISPLAY=:0 && ")

---

### Post by jualansandal on 2008-02-27
Finally, I succeeded. 
I forgot this one "chmod +x *.sh" into the working directory.
Then I changed the task into :
```

/home/hardono/Desktop/Kettle-3.0.1/kitchen.sh -file=/home/hardono/Desktop/Kettle-3.0.1/project/UnzipAllJob.kjb -level=Minimal

```

Thanks for you both supporting me with quick good answer.

but I had something in mind with the function of "export DISPLAY=:0 &&" front parameter, because nothing happened when I add that parameter.
thanks again

---

### Post by northern lights on 2008-02-27
Apparently the problem was elsewhere (as you made you're script executable where necessary).
It seems also, that once executed, the script does the opening of the graphical application - thus it didn't matter after all.
Sorry for having come up with only wrong input...

Had you tried ```
* * * * * /usr/bin/Kettle /.../.../...
``` it woulda needed that entry to ensure output of graphical info...

---

### Post by jualansandal on 2008-02-27
Ok, I will try it, thanks

---

### Post by jualansandal on 2008-02-27
O , one more, and OOT, how to change the title of the topic into [Solved] :D

---

### Post by northern lights on 2008-02-27
Above your first post, check "thread tools"...

---

