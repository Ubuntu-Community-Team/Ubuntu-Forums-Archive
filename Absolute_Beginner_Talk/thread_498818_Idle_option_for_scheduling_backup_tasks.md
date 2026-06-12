---
title: "Idle option for scheduling backup tasks?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by bucketoftruth on 2007-07-11
Is there a way to schedule tasks for when the system is idle, as in nobody is using the keyboard or mouse?  I know how to use cron, but I'm looking for something like the windows (can I say that here?) task scheduler that allows for task scheduling at login/logout and when idle for X minutes.  TIA!

---

### Post by Pragmatist on 2007-07-12
Good question!  You are looking for event-based scheduling, not time-based scheduling.  

**Cron** should work whether your system is idle or not.  For actions on logout, you have a file called **.bash_logout** in your home directory (make sure you include that first ".").  There should be something similar for login, but I don't know what it is.  You can write a custom script and put it in **/etc/init.d** and then create a symbolic link in a runlevel such as **/etc/rcS.d**  

I don't know a general way to schedule based on events, but I would be surprised if it doesn't exist (that is one reason I'm subscribing to this thread--I want to find out!).

---

