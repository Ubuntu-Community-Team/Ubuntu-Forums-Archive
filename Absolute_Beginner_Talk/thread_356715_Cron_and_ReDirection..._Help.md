---
title: "Cron and ReDirection... Help"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Abu Yahya on 2007-02-08
I have installed Ubuntu yesterday after XP crashed. My computer is my alarm clock so I have been doing some reading on how to configure crontab and here is my problem:

cron works fine:
I have scheduled to run cron every minute using this; it will run a script called foo

--$ crontab -l
* * * * *    /home/username/foo

--$more foo
vlc /media/hdb/002.mp3
date > /tmp/this
echo hello

My problem is the first command is not run (vlc will not run); the third command will not run (no output to the screen)

However, my second command runs as schduled and date is redirected to this file which is updated every minute.

When I run the script by itself, all three are running (vlc, date, echo) and I see their outputs. My sound is fine too.

It's making me think that there is some problem with redirection.

Please help.

:confused:

---

### Post by shareMenaPeace on 2007-02-08
Well slightly diffrent but maybe this is intresting too, some notebooks have an automatic startup function inside the bios settings(Set time when to boot the computer),

---

### Post by LotsOfPhil on 2007-02-08
Hmmm. I think it is because cron doesn't send output to stdout. try changing the crontab line to 
```
* * * * * /home/username/foo > output 
```

---

### Post by bruenig on 2007-02-08
> **Abu Yahya said:**
> I have installed Ubuntu yesterday after XP crashed. My computer is my alarm clock so I have been doing some reading on how to configure crontab and here is my problem:

cron works fine:
I have scheduled to run cron every minute using this; it will run a script called foo

--$ crontab -l
* * * * *    /home/username/foo

--$more foo
vlc /media/hdb/002.mp3
date > /tmp/this
echo hello

My problem is the first command is not run (vlc will not run); the third command will not run (no output to the screen)

However, my second command runs as schduled and date is redirected to this file which is updated every minute.

When I run the script by itself, all three are running (vlc, date, echo) and I see their outputs. My sound is fine too.

It's making me think that there is some problem with redirection.

Please help.

:confused:

Try changing the first line to

DISPLAY=:0 vlc /media/hdb/002.mp3

---

### Post by Abu Yahya on 2007-02-08
Thanks for your replies

bruenig, It works... I am really happy that it works does knowing that I have spent hours on this.

I do not understand why though. The DISPLAYis set in my env as DISPLAY=:0
Can anyone exaplin it please?

Also, I tried several things to output the somethin to the terminal and understand it; but none worked. In /dev/ I found that stdout is piped to  /proc/self/fd/1

I tried the following:

--$crontab -l
* *  * * * /home/username/foo

--$ more foo
export DISPLAY=:0
date > /tmp/this
date > stdout
date > /dev/stdout
date >  /proc/self/fd/1
vlc /media/hdb/002.mp3

but nothing is printed out to the screen!! 

date is still being updated in /tmp/this

Thanks

---

### Post by bruenig on 2007-02-09
For whatever reason cron does not recognize your environment's DISPLAY.

As for the rest, it does not print it to the screen because you aren't opening these things in the terminal.

Do "man gnome-terminal" and figure out how to do that. For xfce4-terminal you do
```
xfce4-terminal -e command
```

---

