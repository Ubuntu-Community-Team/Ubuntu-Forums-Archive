---
title: "upgrade to amd64"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by RicktheBrick on 2006-10-21
I just recently upgraded my computer to an amd64 computer and installed ubuntu to it.  I can not do a thing with it.  I had ubuntu installed on a 32bit system and had the following and want to do the same with the 64 bit system.
First I had it set up so it did not require user to login.  I want this since I like to turn computer on and come back to it later and have it ready for use.
Second I had installed boinc on it and can not get it to install on the new system.  I have tried sudo apt-get install and it keeps telling me it can not find package.  It is on the Desktop.
Third I want Boinc to auto start.  
Forth I had it so I could remotely acess the computer using a windows computer so I could shut it down.  I tried to install krdc from the add aplications and after adding it I can not find it anywhere to start it and to put a password on it so I can access the computer remotely.  I can do all of these things and more on a windows computer in less than 10 minutes.  Do not assume any knowledge on my part since I had thought that a terminal was a program for one compter to contact another computer using a phone modem.  It took me hours to figure out that terminal was a command line program.

---

### Post by sumguy231 on 2006-10-21
1.) [http://ubuntuforums.org/showthread.php?t=282188](http://ubuntuforums.org/showthread.php?t=282188)
2.) The packages you'll want are 'boinc-client' and 'boinc-manager'. If you're using KDE, then there's a frontend called kboincspy you could look at too.
3.) Sorry, I haven't used the boinc client. You can probably use cron to automatically start at a specified time:
[https://wiki.ubuntu.com/CronHowto?highlight=%28cron%29](https://wiki.ubuntu.com/CronHowto?highlight=%28cron%29)
4.) If you just want to shut it down, ssh will suffice.
[https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29](https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29)
If you do that, you'll need a Windows SSH client such as puTTY.

---

