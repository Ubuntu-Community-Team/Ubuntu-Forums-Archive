---
title: "Cron doesnt do the jobs"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Mosaab on 2008-04-16
Hi, I am new to cron, maybe I have done some thing wrong or missed something but anyway,

to avoid any mistake in the crontab file, I used the schedule package that comes with ubuntu to edit the crontab file for me.

I used a simple command which is "firefox". but nothing happens. and when I specify that this job runs once in the future, its actually gets executed because when I check the schedule software I dont see it any more .. it disapears exactly at the time specified for the job. but firefox never runs!

I tried simpe jobs too like "ls" , but nothing happened. and dont blame the schedule software cause I tried "crontab -e" but with no result.

what is going on?

Thanks :)

---

### Post by FuturePilot on 2008-04-16
Cron can't launch graphical apps unless you add this to the beginning of the command
```
export DISPLAY=:0 && <command here>
```
So in your case it would be
```
export DISPLAY=:0 && /usr/bin/firefox
```

---

### Post by northern lights on 2008-04-16
cronjobs by default have no graphical output. Run your job like this: ```
* * * * * export DISPLAY=:0 && /usr/bin/firefox
```

The "/usr/bin/" part might be superfluous. Futher, you obviously should put something for one/some of the stars - otherwise a browser will open every minute...

---

### Post by FuturePilot on 2008-04-16
> **northern lights said:**
> cronjobs by default have no graphical output. Run your job like this: ```
* * * * * export DISPLAY=:0 && /usr/bin/firefox
```

The "/usr/bin/" part might be superfluous. Futher, you obviously should put something for one/some of the stars - otherwise a browser will open every minute...

that's right. I forgot. You need to put the absolute path to the program. So it would be /usr/bin/firefox

good catch ;)

---

### Post by Oldsoldier2003 on 2008-04-16
> **Mosaab said:**
> Hi, I am new to cron, maybe I have done some thing wrong or missed something but anyway,

to avoid any mistake in the crontab file, I used the schedule package that comes with ubuntu to edit the crontab file for me.

I used a simple command which is "firefox". but nothing happens. and when I specify that this job runs once in the future, its actually gets executed because when I check the schedule software I dont see it any more .. it disapears exactly at the time specified for the job. but firefox never runs!

I tried simpe jobs too like "ls" , but nothing happened. and dont blame the schedule software cause I tried "crontab -e" but with no result.

what is going on?

Thanks :)

like was mentioned before you need to export the display if you are running a graphical application. here is a [quick and dirty tutorial]("http://ubuntujourney.wordpress.com/2008/03/26/cronjobs-for-dummies-command-line-edition/") for cron jobs.

---

### Post by Mosaab on 2008-04-17
yes that worked thank you very much.

but can any one tell me what this means? just to know?
export DISPLAY=:0 && /usr/bin/firefox

---

### Post by Mosaab on 2008-04-17
And, How can I do it so cron will play an mp3 file in a specific time ?

---

### Post by northern lights on 2008-04-17
The "export DISPLAY=:0" part is responsible for the cronjob to be run as a graphical app on your first display/monitor. If you had two monitors connected (or a laptop with an external monitor) "DISPLAY=:1" would be the other.

The "&&" is an operator. It originally stems from FORTRAN syntax and was a simple "goto", I think. Anyways, it simply is sort of a connector of the two commands.

When you run "firefox" from a terminal or the "Alt+F2" dialog, both "know" where to find the executable. Cron doesn't, so it's gotta be told. The firefox executable simply resides in "/usr/bin/".

---

### Post by Oldsoldier2003 on 2008-04-17
> **Mosaab said:**
> And, How can I do it so cron will play an mp3 file in a specific time ?


```
* * * * * DISPLAY=:0 /path/to/media/player /path/to/media/file
```edit the time and paths as necessary

---

### Post by northern lights on 2008-04-17
That's right.

I'm pretty certain the "export" part is essential though, so it should be ```
* * * * * [COLOR="Red"]export[/COLOR] DISPLAY=:0 /path/to/media/player /path/to/media/file
```

Let's say you use amarok, you have a file called "alarm.mp3" in your home folder and you want it to play every weekday morning at quarter to seven:

```
45 6 * * 1-5 export DISPLAY=:0 /usr/bin/amarok /home/user/alarm.mp3
``` would do just that

---

### Post by Oldsoldier2003 on 2008-04-19
> **northern lights said:**
> That's right.

I'm pretty certain the "export" part is essential though, so it should be ```
* * * * * [COLOR="Red"]export[/COLOR] DISPLAY=:0 /path/to/media/player /path/to/media/file
```

Let's say you use amarok, you have a file called "alarm.mp3" in your home folder and you want it to play every weekday morning at quarter to seven:

```
45 6 * * 1-5 export DISPLAY=:0 /usr/bin/amarok /home/user/alarm.mp3
``` would do just that

export is not necessary-

---

### Post by northern lights on 2008-04-19
I dunno - am willing to believe it isn't.

However, it's now 11:17 AM. I just ran ```
15 11 * * * DISPLAY=:0 /usr/bin/amarok /home/<myuser>/test1.mp3
16 11 * * * export DISPLAY=:0 /usr/bin/amarok /home/<myuser>/test2.mp3
```

Guess what? test2 played, nothing happened a minute before...

Any explanations?

[EDIT]
Correction - I figured it out. I used to run "export DISPLAY=:0 && <command>". If you're daft enough to leave the "&&", as I did, "export" becomes obviously necessary. But that was my brainfart.
[/EDIT]

---

