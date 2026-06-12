---
title: "I cannot get cron to work."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by urIkon on 2007-08-07
For the life of me, I cannot get cron to work. I've looked through all the other "I can't get cron to work" threads, and cannot find a solution. 

I used crontab -e to make a new entry, and after saving am given the output:
```

wram@frankm:/var/mail$ crontab -e
crontab: installing new crontab
```

So no errors in my crontab entry, as it would complain if there were. 

crontab -l outputs:

```
wram@frankm:/var/mail$ crontab -l
56 * * * * /usr/bin/vlc /home/wram/music/mp3/nine\ inch\ nails/\(2007\)\ Year\ Zero/Nine\ Inch\ Nails\ -\ 03\ -\ Survivalism.mp3
```

I know it's wordy, but the command works fine on the command line. Take my word for it.

The odd part is, /var/log/syslog shows cron trying to work, but nothing loads. 

```
Aug  7 06:53:53 frankm crontab[17399]: (wram) BEGIN EDIT (wram)
Aug  7 06:54:49 frankm crontab[17399]: (wram) REPLACE (wram)
Aug  7 06:54:49 frankm crontab[17399]: (wram) END EDIT (wram)
Aug  7 06:55:01 frankm /usr/sbin/cron[15559]: (wram) RELOAD (crontabs/wram)
Aug  7 06:55:02 frankm crontab[17460]: (wram) LIST (wram)
Aug  7 06:56:02 frankm /USR/SBIN/CRON[17523]: (wram) CMD (/usr/bin/vlc /home/wram/music/mp3/nine\ inch\ nails/\(2007\)\ Year\ Zero/Nine\ Inch\ Nails\ -\ 03\ -\ Survivalism.mp3)
Aug  7 06:56:03 frankm postfix/sendmail[17525]: fatal: open /etc/postfix/main.cf: No such file or directory

```

cron is running, for sure. Output from ps aux | grep cron
```

wram@frankm:/etc$ ps aux |grep cron
root     15559  0.0  0.1   3444  1004 ?        Ss   06:23   0:00 /usr/sbin/cron
wram     18431  0.0  0.1   2884   752 pts/0    R+   07:12   0:00 grep cron

```

I've tried it with gedit, echo, a bunch of other GUI and command line programs, and nothing works. 

In case anyone asks, here is my /etc/crontab:

```
wram@frankm:/etc$ cat crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
```

And, my /etc/cron.allow:

```
wram@frankm:/etc$ sudo cat cron.allow
Password:
root
wram
```

There is no cron.deny

This is wracking my brain. HELP!

---

### Post by urIkon on 2007-08-07
Update/bump.

Adding the entry to /etc/crontab has the same results (or lack thereof).
This is making me a sad panda :confused:

---

### Post by schorsch on 2007-08-07
Please try to write a little script:

```
#!/bin/sh
/usr/bin/vlc /home/wram/music/mp3/nine\ inch\ nails/\(2007\)\ Year\ Zero/Nine\ Inch\ Nails\ -\ 03\ -\ Survivalism.mp3

```

and call this script from inside the crontab. Perhaps you can also try to quote the whole command with "" in the crontab.  And if you do not want to get a mail every time the job is done you should add

```
>/dev/null 2>&1
```

at the end of the corresponding line in the crontab. Although it seems, that your postfix is not running .....

---

### Post by urIkon on 2007-08-07
I appreciate the reply, but alas: nothing. With or without quotes, in a script or not. Cron just wont load any commands.

---

### Post by pmg on 2007-08-07
From the  syslog snippet you posted, it is trying to run your command, but it's failing.  The next line after that in the log is it trying to call sendmail, and the most likely reason is to send you mail about the cron failure, but alas sendmail is also failing.  I don't know anything about vlc, but it appears to be a a media player, so I assume it's trying to bring up a GUI.  In order to do that it has to know how to talk to the Xserver.  A program finds that out from the **DISPLAY** environment variable which is set for you at login (or when you start the Xserver in the case of a non-graphical login.)  When a cron job is run, the DISPLAY environment variable isn't automatically set.  I suspect that is the reason the tool is failing.  You could add the following to the shell script you wrote before calling the vlc command:
```
export DISPLAY=:0.0
```
That may do it, unless the tool depends on other environment variables that are set at login.

Even if that does work, it will only work when you are logged into the display.  Only the "owner" of the Xserver can connect to it and open windows on it.

Another approach would be to see if there is a way to run the tool without it opening a GUI, or use another tool that will run from the command line without a GUI.

---

### Post by urIkon on 2007-08-08
worked like a charm. thank you sir. pmg > *

---

### Post by lumiere on 2007-09-07
In my case I also had to set the XAUTHORITY variable. Something like this:

export XAUTHORITY="/home/user/.Xauthority"

---

