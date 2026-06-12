---
title: "crontab &amp; hpodder"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-05-17
any ideas why this doesn't work?  i want to download podcasts to my mp3 player (/media/music) every morning at 5 am.

created with crontab -e (blank lines at end included)
```

steve@darwin:~$ crontab -l
# m h  dom mon dow   command
0 5  * * *       hpodder fetch



```

here's hpodder.conf
```

[general]

; The following line tells hpodder that
; you have already gone through the intro.
showintro = no
[DEFAULT]
downloaddir = /media/music/podcasts


```

i think this config file is correct; when i run "hpodder fetch" from the terminal, everything works fine

thanks

steve

---

### Post by FuturePast on 2007-05-17
You can enable logging for cron in /etc/syslog.conf.

That might help in figuring the problem out.

---

### Post by stevieb on 2007-05-17
thanks,

i removed the comment mark in the /etc/syslog.conf, then changed the hpodder command with crontab -e to run at 8 am.

this still didn't work- and there was no cron.log file created in /var/log either.  what's going on?

---

### Post by FuturePast on 2007-05-17
I believe you will have to restart syslogd.
$ sudo /etc/init.d/sysklogd restart

---

### Post by stevieb on 2007-05-17
ok here we go:

```
cat /var/log/cron.log
May 17 08:48:49 darwin crontab[2008]: (steve) BEGIN EDIT (steve)
May 17 08:49:02 darwin crontab[2008]: (steve) REPLACE (steve)
May 17 08:49:02 darwin crontab[2008]: (steve) END EDIT (steve)
May 17 08:50:01 darwin /usr/sbin/cron[4941]: (steve) RELOAD (crontabs/steve)
May 17 08:50:01 darwin /USR/SBIN/CRON[2042]: (steve) CMD (hpodder fetch)

```

didn't seem to work; i wonder- 2008 in the first three lines- am i telling it to run in the year 2008?

---

### Post by FuturePast on 2007-05-17
I think you should put the full path to the location of hpodder.

---

### Post by stevieb on 2007-05-17
think i got the path right:

cat /var/log/cron.log

```

May 17 10:07:01 darwin /usr/sbin/cron[4941]: (steve) RELOAD (crontabs/steve)
May 17 10:09:01 darwin /USR/SBIN/CRON[5235]: (steve) CMD (\usr\bin\hpodder fetch)
May 17 10:09:01 darwin /USR/SBIN/CRON[5234]: (steve) MAIL (mailed 34 bytes of output but got status 0x0001 )
May 17 10:17:01 darwin /USR/SBIN/CRON[5490]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 17 10:26:57 darwin anacron[5818]: Anacron 2.3 started on 2007-05-17
May 17 10:26:57 darwin anacron[5818]: Normal exit (0 jobs run)

```

---

### Post by FuturePast on 2007-05-17
[COLOR="Red"]/[/COLOR]usr[COLOR="Red"]/[/COLOR]bin[COLOR="Red"]/[/COLOR]hpodder fetch

---

### Post by stevieb on 2007-05-17
still no luck, although it seems to be executing the command:
```
May 17 12:10:01 darwin /usr/sbin/cron[4941]: (steve) RELOAD (crontabs/steve)
May 17 12:11:01 darwin /USR/SBIN/CRON[8742]: (steve) CMD (/usr/bin/hpodder fetch)

```

i thought that hpodder might be hanging for some reason, so i changed the directory to my desktop, but it still doesn't seem to work with crontab, although it works from the command line manually.

---

### Post by FuturePast on 2007-05-17
I've just set this up as you've described and it works for me.
Bear in mind that cron sends any command output by email, so I suggest installing sendmail
$ sudo apt-get install sendmail

and adding a line
MAILTO=my@email.com

to your crontab, so that any results are sent to you.

Also at the time hpodder is supposed to run, type ps -e to make sure it actually is running, and the numbers in the cron.log e.g. [2008] refer to process ids.

---

### Post by stevieb on 2007-05-17
i think i might have it working now; the problem seems to have been in hpodder.conf.  i want the podcasts to go directly to the mp3 player (trekstor vibez), and it took me a bit to get the directory right.  if it works tomorrow morning, i'll post both config files (hpodder and my crontab) for reference.  thanks for all your help!

-steve

---

### Post by mohawk82 on 2007-06-23
Did your fix work?

I am trying to set op a 0400 daily hpodder download.

Thanks for steering me in the right direction.

Mohawk82

---

### Post by stevieb on 2007-06-23
it didn't work, but i found another solution.  rather than using crontab -e, i edited the file /etc/crontab.  in that file is an extra field where you put your username.  here's my file:```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=[username]@email.com

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
0  5    * * *   steve   /usr/bin/hpodder fetch



```

so, this is set to execute the command "hpodder fetch" every day at 5 am.  hope it helps!

-steve

---

### Post by mohawk82 on 2007-08-07
It has been working great!  Thank you very much.

Mohawk82

---

### Post by mister_p_1998 on 2007-09-12
If Hpodder is a GUI program, you need to put the folllowing line BEFORE the path to the program:

export DISPLAY=:0 &&

(Upper case on DISPLAY)

Steve

---

