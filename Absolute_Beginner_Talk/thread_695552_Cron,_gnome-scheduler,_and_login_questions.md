---
title: "Cron, gnome-scheduler, and login questions"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-13
I have a few questions about the aforementioned.

Is gnome-scheduler just an interface into cron?  If so, would there be any reason (other than learning about cron) to use cron as opposed to gnome-scheduler?

If I have my PC turned on, but sitting at the login screen, will cron still work?  I guess this is more of a general question about Ubuntu... do I need to be logged in.. or will ssh, cron, azaeurus, etc work without being logged in?

---

### Post by kpkeerthi on 2008-02-13
> 
Is gnome-scheduler just an interface into cron? If so, would there be any reason (other than learning about cron) to use cron as opposed to gnome-scheduler?
   Yes, well actually it is an interface to **crontab** . Unfortunately, gnome-scheduler did not work when I tried to add an one-time-job and it printed too much of cryptic error messages to the console. Open it from a terminal and try it for yourself. May be you are lucky.

> 
If I have my PC turned on, but sitting at the login screen, will cron still work? I guess this is more of a general question about Ubuntu... do I need to be logged in.. or will ssh, cron, azaeurus, etc work without being logged in?

   Not in front of linux right now. If I were you, I would write a script that prints "Hello" to a file and schedule it to run in 5 minutes. Restart/Logout and check back after 5 mins.

---

