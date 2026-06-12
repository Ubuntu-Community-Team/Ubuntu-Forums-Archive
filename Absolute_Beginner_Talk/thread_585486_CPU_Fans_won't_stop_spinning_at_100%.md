---
title: "CPU Fans won't stop spinning at 100%"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by mitchlourens on 2007-10-21
When I run my machine under windows, it is always silent unless under a heavy load, but under Ubuntu 7.10, they don't' seem to ever slow down to anything lower than 100%.  I think it might be a driver issue, although I'm not entirely too sure.  I also don't know what kind of information I'm supposed to put on here, so if anyone is willing to help me out, and tell me what I need to post and how to acquire it, I would greatly appreciate it.

---

### Post by Vansinnesvisan on 2007-10-22
One way to control the speed of fans in your computer is to use lm-sensors. It will throttle the fan speeds based on the temperatures. 

Here is a [How to]("http://ubuntuforums.org/showthread.php?t=42737&highlight=lm+sensor+cpu+fan+speed") guide to set it up.

It is a little time consuming to set up, but it works well in my experience.

---

### Post by Paul820 on 2007-10-22
It might be tracker indexing your files, it's doing it to me now. Have a look at the System Monitor and see what processes are running.

---

### Post by mitchlourens on 2007-10-22
> **Paul820 said:**
> It might be tracker indexing your files, it's doing it to me now. Have a look at the System Monitor and see what processes are running.
All my processes are sleeping except for gnome-system-monitor.  Its kinda weird because the fans are on all the time, no matter what kind of a load i've got it running, even when i'm not even logged in, that is what leads me to believe that its a driver issue.  I wonder if the updates that i'm about to download will help at all..

---

