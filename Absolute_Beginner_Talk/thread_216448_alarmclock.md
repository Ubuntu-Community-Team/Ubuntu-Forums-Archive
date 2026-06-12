---
title: "alarmclock"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by linuxfan3 on 2006-07-15
Hi to you all,:) 
excuse my english but i need help with installing an "alarmclock" on dapper.here my imagine:

At a defenite time the PC boots and the acountlogin gets automatically done by a programm ( for example winamp on windows) then an autostarting script opens a musicplaylist....So i need 1.)something that makes the PC booting 2.) a programm for autologin and 3.) an autostarting script.i've no idea how to realize?! please help!:-k 
thanks a lot!

Jonas

---

### Post by christhemonkey on 2006-07-15
Well i imagine mpd would be the way to go for an alarm clock.
```
sudo apt-get install mpd gmpc 
```
Gmpc is a graphical frontend, as it is a command line utility.

I imagine that the best way to get it working as an alarm clock would be to use a cron job.
```
crontab -e
```
Then it should allow you to edit your crontab, adding this line to the end;
```
0 07 * * 1-5    mpd ~/alarmnoise.wav 
```
This plays alarmnoise.wav at 7:00 on weekday mornings.
Read crontab's manfile for more information on howto use cron.
```
man crontab 
```
Then save and close your edited crontab.

As for powering your computer on to do this, i dont have a clue im afraid.

---

