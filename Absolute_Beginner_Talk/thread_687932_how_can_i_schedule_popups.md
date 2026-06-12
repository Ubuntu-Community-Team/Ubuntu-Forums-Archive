---
title: "how can i schedule popups?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2008-02-04
I'm taking boxing lessons, and the weekly schedule is very erratic. Mondays its at 6:45, Tuesday is's 6:45 and 8PM, Wednesday it's 5:30 and 8PM, etc. Its very hard to keep track of when the lessons are, especially for me since I work at home, and rarely know what day of the week it is anyways.

When I was in college I used this program called Rainlender which I had programed to make popup messages 10 minutes before each of my classes start times to remind me. It would be great if there were a program for Ubuntu that would do the same thing for me and my boxing lessons.

I know about cron, but I don't know how to make it launch popup reminders.

---

### Post by Dr Small on 2008-02-04
Crontabs and Zenity could get the job done

---

### Post by FuturePilot on 2008-02-04
Yes Cron and Zenity will work great.
Zenity is pretty straight forward. See the man page, it will tell you everything you need to know. 
It usually goes "zenity" "popup type" "popup title" "popup text"
For example
```
zenity --info --title="Information" --text="Hello World"
```
That will just display a little Info popup.
There's various types of popups you can make. It's all explained in the man page
```
man zenity
```
However if you put a Zenity command into Crontab, it won't work since Cron cannot launch graphical stuff unless you tell it to use a screen. You do this by prefixing the command you want to run with
```
export DISPLAY=:0
```
:0 is the default display. If you screen is something other than :0 adjust it accordingly.
So if you were to put the Zenity example from above into Crontab it would look something like this
```
export DISPLAY=:0 && zenity --info --title="Information" --text="Hello World"
```
Also if you're looking for a nice GUI for Crontab, check out Gnome Schedule
```
sudo apt-get install gnome-schedule
```

---

### Post by y-lee on 2008-02-04
There is a [timer-applet]("http://timerapplet.sourceforge.net/") that one can add to a panel. It is easy to use tho for some reason I can't get the sound to work in Dapper. But it will pop up a window at a certain preset time and it's in the repos :)

---

