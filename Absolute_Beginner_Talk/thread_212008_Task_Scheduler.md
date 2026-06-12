---
title: "Task Scheduler"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-07-09
hi all.

is there a built in GUI scheduler in ubuntu? breezy or dapper?

quick simple question. i'm probably missing something very obvious.

cheers

---

### Post by woedend on 2006-07-09
no...and I wish there was(at least, the last time I checked, there wasn't by default).  
you can install the package gcrontab, but its very rudementary and ugly.  The easiest way to do it is by hand honestly I have found.  
I don't know your skill level, but just in case you don't know how to make tasks and more importantly to any new users who need to know...I like to do it as such from a terminal
gedit mytasks

now you get a nice gui empty pad.  here is the order for tasks
min hour day date(1-31) month(1-12) dayofweek(0-6) command



so lets say you want an alarm clock to play alarm.mp3 every morning at 1 PM, you would make a line

00 13 * * * xmms "alarm.mp3"

hours must be written in military time, use the character * for ALL/ANY.  so this reads at the 00 minute of the 13th hour of any date, month, and day of the week, run xmms "alarm.mp3".


once you get the hang of it, save the file, close it, and issue the command
crontab mytasks
replacing the word mytasks with whatever it is you saved your original file as.

(note - you can also do this using crontab -e, but i found this method easier for me personally.)

just to make sure it saved and will work, when finished, issue the command crontab -l
it should be listed there...if not there may be a problem.
One other thing to note...you cannot use cron to launch a GTK application(or any GUI).  The only way the xmms command above works is if xmms is alreay open.  otherwise you would want to use a commandline tool to play the song.

---

### Post by ProjectGod on 2006-07-09
Thankyou very much for this thorough answer!! :D if the developers regularly skim these forums i hope they find this tread so they do include an easy to use GUI task scheduling tool.

Cheers!

---

### Post by woedend on 2006-07-09
@project - don't count on it.  i've asked in these forums since hoary for this every time a suggestion thread came up.  It would be very simple to write a frontend for this(KDE has one), i'm not sure why it's not included in gnome by default.  Unfortunately, I have no programming talents with linux, so I don't complain much since i'm not contributing.

But, rather than using just a frontend for crontab, it would be nice to have a full featured daemon/frontend that WILL launch any command, including Gtk apps.

---

### Post by struess on 2006-07-12
hey woedend,
thanks for the help.. after some tinkering, xmms is scheduled to gently wake me up each morning.  note to whoever else tries this (i used **crontab -e** rather than a text editor), you need the whole path and filename on *one line* in the command column.. crontab -e kept splitting the command into two lines and then refusing to write the file when i saved it... its gotta be on the same line. 

another question:  the crontab entry on the ubuntu documentation site mentioned a scheduled echo command.. when crontab runs, where does this echo show up?  i  had a terminal open at the time of testing, but no message showed up.  sneaking on to friends' systems and leaving them scheduled messages would be entertaining ;) 

crontab -l produces: 
```
johnk@struess:~$ crontab -l
# m h  dom mon dow   command
57 11 * * * echo "hiiiiiiiiiiiiiiiiiiiiiii"
57 11 * * * xmms "/home/johnk/music/alternative_harder/A Perfect Circle/13th step/A Perfect Circle-Thirteenth Step-03 - The Noose.mp3"

```

---

