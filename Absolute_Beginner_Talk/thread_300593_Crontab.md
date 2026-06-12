---
title: "Crontab"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by nhandler on 2006-11-15
I am trying to learn how to work with the crontab. I used 'crontab -e' to edit it based on what the wiki said. When I type 'crontab -l' here is the output:

> 
0,15,30,45 *  * * *   import -window root ~/ScreenShot.png >> /home/cheater/crontabss.log
0 0 * * *   /usr/bin/apt-get update >> /home/cheater/crontabagu.log
* * * * * wall "Testing" >> /home/cheater/crontabtest.log


The idea is that the screenshot command is run every 15 minutes. The apt-get update is run at midnight daily. The Testing thing was a test. None of them run. The log files are all blank, so I assume that means there are no errors. I know the actual commands are good (except for the wall command. I took that from the wiki. I have no idea what that does).

Could someone please help me get this working? I really would like to know how to use this. Thanks.

---

### Post by moshuptrail on 2006-11-15
start simple

* * * * * echo "test" >> /home/cheater/test.log

I set this in my user crontab and it worked just fine.

The wall command writes to users terminals who are using Terminal at the time.  I don't know it it puts anything in the log, but I doubt it.

The import command???  Don't know what that is.

---

### Post by David_T on 2006-11-15
If you want to do a crontab for apt-get, it would need to be in root's crontab, because you can't do sudo in a script.

By default the output of your crontab entries gets emailed to you (the Unix ``mail'' command), but Ubuntu doesn't have that by default.

But, of course you can redirect output.  If you want to send all output from a command (stdout and stderr) to logfile, just type command &>logfile.  Just stderr would be 2>logfile.

Oh and if you want to do a command that opens a window in your crontab (say you want to open gimp) you need to do it like so:
export DISPLAY=:0 && gimp

---

### Post by nhandler on 2006-11-16
> **moshuptrail said:**
> start simple

* * * * * echo "test" >> /home/cheater/test.log

I set this in my user crontab and it worked just fine.

The wall command writes to users terminals who are using Terminal at the time.  I don't know it it puts anything in the log, but I doubt it.

The import command???  Don't know what that is.

The echo command worked. It showed Test in the log file. The import command is something I found online. It is meant to take a screenshot.



I checked the root crontab, and it had:
> 0 0 * * * apt-get -y update && apt-get y upgrade && apt-get -y dist-upgrade && apt-get -y clean


What do the -y things do?

---

### Post by petef on 2006-11-16
Automatically answers yes to prompts

:)

---

