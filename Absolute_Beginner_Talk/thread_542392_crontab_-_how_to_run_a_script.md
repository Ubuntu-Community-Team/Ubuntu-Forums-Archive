---
title: "crontab - how to run a script"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by adhg on 2007-09-03
I'm trying to test the crontab functionality. 
for this I did the following:
1. I create a simple script under /home/adriana/scripts/test.sc

(this file does: echo testing....1.2..3)

2. I created the crontab as follow:

# m h  dom mon dow   command
10 21 * * * bash /home/adriana/scripts/test.sc

I assumed the script will run on 9:10pm...but it didn't.
I also tried without the bash:
10 21 * * * /home/adriana/scripts/test.sc

...same result

thanks for any pointers.

---

### Post by ericmitz on 2007-09-03
did you give test.sc executable rights?

---

### Post by adhg on 2007-09-03
I did. (right click and checked the Is executable on the permission tab)
still...same result (nothing) :confused:

---

### Post by lloyd_b on 2007-09-03
> **adhg said:**
> I'm trying to test the crontab functionality. 
for this I did the following:
1. I create a simple script under /home/adriana/scripts/test.sc

(this file does: echo testing....1.2..3)

2. I created the crontab as follow:

# m h  dom mon dow   command
10 21 * * * bash /home/adriana/scripts/test.sc

I assumed the script will run on 9:10pm...but it didn't.
I also tried without the bash:
10 21 * * * /home/adriana/scripts/test.sc

...same result

thanks for any pointers.

Question:  What *exactly* is your test script doing?  A simple 'echo "1 2 3"' (i.e. console output) will not do anything detectable unless you have your system configured to email you the cron output (No, it will *not* open up a terminal window, nor will it display on the system console).

If so, instead of the simple echo, redirect it to a file:
```
echo "Testing 1 2 3" > /home/adriana/scripts/test.result
```
and then check that directory after the appropriate time and see what if that file was created.

Lloyd B.

---

### Post by yabbadabbadont on 2007-09-03
Make sure that you set the HOME directory and the PATH that the script needs while running in your crontab.  Here is one of mine as an example: ```
/home/daffy $ cat crontab 
HOME=/home/daffy
PATH=/home/daffy/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
# m h  dom mon dow   command
*/11 * * * * wallpaper-list-create > /dev/null 2>&1
*/5 * * * * wallpaper-set-random > /dev/null 2>&1

```

---

### Post by adhg on 2007-09-03
Thanks lloyd_b!!! yes, that did it.

On a different note, I'm reading a book that specifies the following (continue to the crontab)

SHELL=/bin/bash
PATH=/sbin:/bin:/user/sbin:/user/bin
MAILTO:adriana
HOME=/home/adriana

My question is: where does all the setup of MAILTO is configured, so I can create a crontab with: mail [email]adriana@mydomain.com[/email]

thanks!

---

### Post by lloyd_b on 2007-09-04
> **adhg said:**
> Thanks lloyd_b!!! yes, that did it.

On a different note, I'm reading a book that specifies the following (continue to the crontab)

SHELL=/bin/bash
PATH=/sbin:/bin:/user/sbin:/user/bin
MAILTO:adriana
HOME=/home/adriana

My question is: where does all the setup of MAILTO is configured, so I can create a crontab with: mail [email]adriana@mydomain.com[/email]

thanks!

First off, you'll need to have a Mail Transport Agent (MTA) installed (I believe that "exim" is the "default" MTA for Ubuntu, though there are others, including "sendmail").

Second, you'll have to properly configure said MTA.  Don't ask me how - I haven't a clue.

But here's a link that should help: [How to configure Exim]("http://newbiedoc.sourceforge.net/networking/exim.html")

Lloyd B.

---

### Post by yabbadabbadont on 2007-09-04
If you only want to have it mailed to a user on the local machine, it is usually easier to install postfix.  When the post installation config is automatically run, just choose the option for "local machine only".

---

