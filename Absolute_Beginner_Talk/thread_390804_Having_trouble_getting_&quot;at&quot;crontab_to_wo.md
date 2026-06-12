---
title: "Having trouble getting &quot;at&quot;/crontab to work"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-22
Hi guys,

I was trying to setup "at" or crontab for an alarm, but I could never get it to execute whatever I wanted it to.

For example:
```

kinson@ubuntu:~$ at now
warning: commands will be executed using /bin/sh
at> rhythmbox --play-pause
at> <EOT>
job 15 at Fri Mar 23 00:39:00 2007
kinson@ubuntu:~$

```

I expected the above code to toggle the play/pause of rhythmbox straightaway, but its not doing anything. Same happens when I set it for a different time. After the time, the job disappears, but nothing happens. I've tried entering the "rhythmbox --play-pause" command into a text file, and made it executable (via nautilus, right click ->properties), and piping it in, but it still doesn't work :(

I have the same problem with crontab:

```

ckinson@ubuntu:~$ crontab -l
# m h  dom mon dow   command
43 0 * * * rhythmbox --play-pause
44 0 * * * /home/kinson/.job
kinson@ubuntu:~$

```

More or less its supposed to :

@00:43 run rhythmbox--play-pause
@00:44 run ./job (not sure whether thsi would work, but I tried it anyways).

Any idea what I'm doing wrong here? :(

Cheers,
Kinson

---

### Post by kinson on 2007-03-23
I was reading some of the other posts around the forum, and somebody mentioned that they needed to install "mailx" before it worked. Is this really necessary? :(

I still haven't been able to get at/crontab to work. I can understand myself mucking up crontab for some weird reason, but I really can't seem to understand how I can screw up "at".

I've been searching all over, and every page has more or less the same advice. Doesn't say anything needs to be installed or setup first.

I've also setup an at.allow file:

```

kinson@ubuntu:~$ cat /etc/at.allow
kinson
kinson@ubuntu:~$

```

But it doesn't seem to help :(

Please guys,
Any suggestions? :(

---

### Post by fac on 2007-03-23
If you add the following to your crontab file it will work

```
MAILTO=""
```

see this thread: [http://www.ubuntuforums.org/showthread.php?t=362449]("http://www.ubuntuforums.org/showthread.php?t=362449")

---

### Post by kinson on 2007-03-23
Thanks, but I tried that before...unless I'm not getting it right.

```

kinson@ubuntu:~$ crontab -l
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h  dom mon dow   command
MAILTO=""
59 22 * * * rhythmbox --play-pause
44 0 * * * /home/kinson/.job

kinson@ubuntu:~$

```

Below is my "cat /etc/crontab":
```

kinson@ubuntu:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#


kinson@ubuntu:~$


```

Any help? :(

Thanks,
Kinson

---

### Post by fac on 2007-03-23
I just had the problem myself, and for me it worked to do this in my user crontab.

```

MAILTO=""

# m h  dom mon dow   command
59 22 * * * rhythmbox --play-pause
44 0 * * * /home/kinson/.job
```

and in the global /etc/crontab/ i have also put a MAILTO="" below the PATH variable

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=""

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

```

but it didn't work to just put it in their so I don't know if that is neccessary (I did a reboot after this edit).

---

### Post by kinson on 2007-03-25
Adding the "MAILTO=""" in both files didn't make it work either :(

my crontab:

```

kinson@ubuntu:~$ crontab -l
# m h  dom mon dow   command
MAILTO=""
21 23 * * * rhythmbox --play-pause
21 23 * * * echo "hello world"

kinson@ubuntu:~$

```

My systemwide crontab:
```

kinson@ubuntu:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=""

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#


kinson@ubuntu:~$

```

Any other suggestions? :( I'd greatly appreciate this. I'm not sure whether its related, but as I mentioned earlier, my "at" command isn't doing anything, even stuff like "echo hello" or whatever.

My friend said it might be a permissions problem, could that be it? But if it were a permission problem, there would be an error prompt right? The irritating thing is that nothing happens, and there are no error messages, so I don't know what is going wrong here :(

Please help,
Kinson :confused:

---

### Post by nerubian on 2007-05-12
UP UP!, 
I couldnt make crontab work either, I tried lots of commands hours and hours still Not even 1 of them worked.What's happening?

I also tried KCron (a graphical KDE app to edit cron file) still my commands like usr/bin/amarok didnt worked once.Any suggestions and information?

---

### Post by nerubian on 2007-05-12
can someone explain the work principle of this cron program?

I thought that you enter the values correctly and add program like /usr/bin/amarok and it would run it on time.But I have never seen it worked.Do we need scripts for applications installed in system?Isnt the path enough?

an example

56 5 * * *    /usr/bin/amarok

I think this entry should run amarok at 5:56 am everyday.am i wrong?or we can fill "*" with approriate time settings like " 56 5 12 5 6 "for today to run the app just for today?

---

### Post by kinson on 2007-05-13
I'm currently using:

```

37 02 * * * export DISPLAY=:0 && rhythmbox-client --play-pause

```

at 2:27am everyday start rhythmbox. I'm not sure why I need the "export DISPLAY=:0" at the start, but it seems to do the trick(though it launches a new instance of rhythmbox).

I couldn't get it to work in Dapper, but its working in Feisty.

I don't think you need to put the full path, you could probably just use:
```

56 5 * * * export DISPLAY=:0 && amarok -p

```

I'm not sure whether that "amarok -p" is the correct command, but just substitute it with whatever you want.

Let me know if that can help.

Cheers,
Kinson

---

### Post by nerubian on 2007-05-13
hey

```
02 16 * * * export DISPLAY=:0 && amarok
```

This entry could start amarok in specified time.without "-p" command.I am using feisty too, I haven't tried this on dapper and edgy but it works now.what an interesting trick!Thanks very much.

i dont know much about commands, do you know something about "export DISPLAY"  thing?

---

### Post by kinson on 2007-05-13
I think it has to do with amaroK being a GUI program.

You should check out this thread: [http://ubuntuforums.org/showthread.php?t=185993&highlight=crontab]("http://ubuntuforums.org/showthread.php?t=185993&highlight=crontab")

I thought the amaroK argument to play a song was "-p" thats why I put it there, apologies :) I can't remember its commands, and I don't have it installed here, hehe ! :)

Anyways, glad you got it working ! :)

Cheers,
Kinson

---

