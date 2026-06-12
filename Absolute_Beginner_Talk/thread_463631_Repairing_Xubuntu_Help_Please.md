---
title: "Repairing Xubuntu Help Please"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Airais on 2007-06-03
okay I have an old desktop I use simply to surf the net and download files I feel might be shady (as far as virus and spy-ware) with Xubuntu as Ubuntu is a little to slow for my taste.  I love it however while downloading a particular large file (oh about 10 gigs, not kidding) I found that the system had crashed or something close to that as I turned on the screen to find that I was back at the log-on screen.  So not too worried I logged back on to re-start the download only to find that the top panel was broken.  By this I mean that insted of going across the top it stoped halfway and some of the buttons were unresponsive.  Having decades you Windows experence I simply shut down the system (the proper way) and after waiting a few seconds rebooted only to find that now the desktop gone.  Fustrated I re-rebooted (this time just clicking off the powerbar I have it connected to) and loaded it up and loged on to find the desktop back but the top panel still broken.  The system seems to work find other wise with one exception I went to re-install the panel program using synaptic and it asked for the CD no biggie I open the CD drive and put it in and clicked okay but nothing happen. I wait and try again thing the computer haden't read the CD yet, nothing.  The CD come up on the file system and I can access the files there but synaptic doesn't read it.  I though about booting the system off the CD and choosing Repair but I am afraid of loosing and or it messing up the 7 gigs of data that did download PLEASE HELP!!!!!!

---

### Post by john.nicholls on 2007-06-04
When you have Xubuntu running, open a terminal and type
```
xfce-setting-show
```
to bring up all the options.Have at a look at the options under Panel to see if they solve your problem with the panel.

---

### Post by ugm6hr on 2007-06-04
or:

```
xfce4-panel
```

that brought up my panel options for me when I couldn't find it.

---

### Post by Airais on 2007-06-04
Your answers are nice but I forgot to mention I am having the same terminal problem as every other Xubuntu user is in that it simply logs me out every time I try to access the terminal, but thanks

---

### Post by john.nicholls on 2007-06-04
> **Airais said:**
> Your answers are nice but I forgot to mention I am having the same terminal problem as every other Xubuntu user is in that it simply logs me out every time I try to access the terminal, but thanks

You're exaggerating a bit; I have no trouble with Xubuntu and the terminal. Have you tried using the Xfce terminal or just using ctrl-alt-F1?

---

### Post by Airais on 2007-06-04
um NO I AM NOT...... every thing I descrided is happening and yes I have tried both and if YOU did you research you would find that the terminal problem is a known issue they are working on.

---

### Post by ugm6hr on 2007-06-05
There are solutions to your Terminal problem:

[http://ubuntuforums.org/showthread.php?p=2694416](http://ubuntuforums.org/showthread.php?p=2694416)

Presumably your hardware is not good enough to install from the LiveCD?

As for restoring the panel:

Open Thunar ("Home") and go to /usr/bin/xfce4-panel (double click)
Hopefully that should work.  If not, try it from Terminal (maybe with sudo) if you manage to get that sorted.

As for retrieving the downloaded file - which download manager were you using?  If it was the built in Firefox one, I am not sure there is any way to restart from a part download.

---

