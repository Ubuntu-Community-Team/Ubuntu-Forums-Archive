---
title: "Linux Mint 13. Cron task is not working"
date: 2012-08-03
forum: Any Other OS
---

### Post by retano on 2012-08-03
Hello all,

For some reason my cron job will not run. This is my setup:
retano@OptiPlex-GX520 ~ $ pgrep cron
902
retano@OptiPlex-GX520 ~ $ crontab -l
0 * * * * mate-terminal # JOB_ID_4
retano@OptiPlex-GX520 ~ $ mate-terminal
retano@OptiPlex-GX520 ~ $

So  it is just a simple command to get a new terminal window and it is  not working. When I run it directly from terminal - it is opened  ok. 

Please advise what can be wrong here?

---

### Post by spjackson on 2012-08-03
Is this just a test, or do you have some reason to start a new terminal like this?

cron isn't related to a desktop session; it is for tasks that run in the background so long as the computer is running, whether a user is logged in or not. The cron job has nothing to tell it on which desktop to put the window.

It *may* be possible to set the DISPLAY variable and get it to work - I'm not sure. I wouldn't recommend you to go down that road though, unless you have a genuine need.

---

### Post by retano on 2012-08-04
I am trying to get my Sikuli scripts working. They were running Ok with Mint 10, but I can't get it working with Mint 13. I also tried to use Gnome schedule as a GUI for cron setup - it did not help also.

This is headless PC with no monitor attached. I operate with it via VNC session

---

### Post by spjackson on 2012-08-04
I'm not on Mint, but this works for me. In vnc session, start a terminal, and
```

$ echo $DISPLAY
:1.0

```Then create a cron job with crontab -e
```

0 * * * * DISPLAY=:1.0 /usr/bin/lxterminal

```

---

### Post by Perfect Storm on 2012-08-04
Moved to Other OS/Distro Talk.

---

### Post by retano on 2012-08-10
> **spjackson said:**
> I'm not on Mint, but this works for me. In vnc session, start a terminal, and
```

$ echo $DISPLAY
:1.0

```Then create a cron job with crontab -e
```

0 * * * * DISPLAY=:1.0 /usr/bin/lxterminal

```
Does not work :(
this is my output:
$ echo $DISPLAY
:0.0
so I insert it like this 0 * * * * DISPLAY=:0.0 mate-terminal

---

### Post by spjackson on 2012-08-10
I have just tried it with a Mint 13 Live CD. It works for me. DISPLAY is :0 in this case.
```

0 * * * * DISPLAY=:0 mate-terminal     

```I don't know why it won't work for you. Is there any clue in /var/log?

---

### Post by retano on 2012-08-12
I really don't understand what is wrong here. Tried to create a logfile with output, this is the current setting:

1 * * * * DISPLAY=:0 mate-terminal exec >> /home/log/terminal.log 2>&1

but I don't have the log file created. Why?

---

### Post by spjackson on 2012-08-12
> **retano said:**
> I really don't understand what is wrong here. Tried to create a logfile with output, this is the current setting:

1 * * * * DISPLAY=:0 mate-terminal exec >> /home/log/terminal.log 2>&1

but I don't have the log file created. Why?
Does the directory /home/log/ actually exist and is it writable by you? Does this work from a terminal?
```

echo hello >> /home/log/terminal.log

```
Is cron running? Is a CRON entry written to /var/log/auth.log when the jobs is meant to run?

---

### Post by retano on 2012-08-12
> **spjackson said:**
> Does the directory /home/log/ actually exist and is it writable by you? Does this work from a terminal?
```

echo hello >> /home/log/terminal.log

```Is cron running? Is a CRON entry written to /var/log/auth.log when the jobs is meant to run?

oops I missed my login name:
echo hello >> /home/retano/log/terminal.log 
is working Ok from terminal, but not as a cron job
1 * * * * DISPLAY=:0 mate-terminal exec >> /home/retano/log/terminal.log 2>&1

CRON service is running Ok:
retano@OptiPlex-GX520 ~ $ pgrep cron
936

last entries from /var/log/auth.log:
Aug 12 19:17:01 OptiPlex-GX520 CRON[13725]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 12 19:17:01 OptiPlex-GX520 CRON[13725]: pam_unix(cron:session): session closed for user root
Aug 12 19:39:01 OptiPlex-GX520 CRON[13749]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 12 19:39:03 OptiPlex-GX520 CRON[13749]: pam_unix(cron:session): session closed for user root
Aug 12 20:01:01 OptiPlex-GX520 CRON[13756]: pam_unix(cron:session): session opened for user retano by (uid=0)
Aug 12 20:01:01 OptiPlex-GX520 CRON[13756]: pam_unix(cron:session): session closed for user retano
Aug 12 20:09:01 OptiPlex-GX520 CRON[13761]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 12 20:09:03 OptiPlex-GX520 CRON[13761]: pam_unix(cron:session): session closed for user root
Aug 12 20:17:01 OptiPlex-GX520 CRON[13769]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 12 20:17:01 OptiPlex-GX520 CRON[13769]: pam_unix(cron:session): session closed for user root
Aug 12 20:39:01 OptiPlex-GX520 CRON[13843]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 12 20:39:02 OptiPlex-GX520 CRON[13843]: pam_unix(cron:session): session closed for user root

---

### Post by spjackson on 2012-08-12
So the auth.log shows that cron has seen and executed your job. I'm out of ideas now I'm afraid.

---

### Post by JaM0N on 2012-11-11
Did you find a workarround for this?? Im going mad trying to change background from cron!!! 

Ive tried almost every combination of DISPLAY, XAUTHORITY, env, os.environ, export, &&, you can not imagine how many tries i did with this!!!

So if you have found a way to exit this loop of desperation, please enlighten us :D

---

### Post by retano on 2012-11-12
It did not work for me even after I reinstalled the OS itself. But in different version of Mint = XFCE ver. 13 it worked like I wanted it to and with no additonal manipulation from my side. Perhaps you may try the other desktop environment...

---

