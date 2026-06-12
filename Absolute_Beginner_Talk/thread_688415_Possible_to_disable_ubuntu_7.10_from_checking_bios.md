---
title: "Possible to disable ubuntu 7.10 from checking bios time when login?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by soonsoon on 2008-02-05
HI all


my cpu does not come with a batt for bios clock, the internal goldcap on board can only ensure the bios clock to be running for 5 day. if i shutdown the pc for more than 5 day, I will be prompt to change the time or ignore when i auto login.


is it possible to ignore the checking of the bios when login?
I am using Ubuntu for some embedded application, i need my application to startup themselves, but with the prompting of the checking of clock, the whole process is disrupted.


or any one can advice me a better way to run my application? I need my application to run on startup, and with remote access capability from other terminals.

I am pretty new to ubuntu, can any one advice me on this

thanks in advance

regards
soonsoon

---

### Post by ukripper on 2008-02-05
Why don't you create a cron job (specify time or days) and put your job at startup.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)


here is the gui version incase you like [http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

---

### Post by rkd on 2008-02-05
I don't completely understand the situation, so these ideas might not prevent the prompt you mention. If they aren't helpful, sorry for the bad suggestion.

If it doesn't matter that the system date and time be correct, perhaps you could put a command something like this:```
date -s "1 JAN 2008 00:00:00"
```into one of the system startup scripts.

If you need the time to be approximately accurate and you have access to the network at startup time, perhaps you could put an ntpdate command into one of the system startup scriptions, or configure the ntpd service.

---

### Post by soonsoon on 2008-02-06
Hi

I am using ubuntu to run some of my application. this applications is needed to be ran straight after startup. so if the prompt for user to adjust time pop out, then my application will not run as i place application to start running when the session start.

maybe i should just place my application in rc.local.

just a side question. if my application is a endless loop, and i place it in rc.local, will ubuntu still start up?

any way i have tried your suggestion, it work, but i just have to bare with the time :) thank you very much

---

### Post by rkd on 2008-02-06
I think you can start your application in rc.local without preventing the startup from completing if you put an & at the end of the command.

---

