---
title: "Cannot start any application"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by higuava on 2007-11-06
I am new to Linux. I am on Ubuntu 7.10.
After I leave the computer on for a while without using it, I can't run any application anymore. If I try to start an application, I will see a new tab at the bottom panel and the cursor changes to the waiting shape. However, the application will not really start and the tab at the bottom will disappear. I have to restart the system at this point. After restart, I looked for logs using the log tool. I don't see anything special in /var/log. However, this problem will never happen if I keep using the computer.

---

### Post by ROBarber on 2007-11-06
do you have setup for hibernate or suspend state?

---

### Post by higuava on 2007-11-06
I don't know if I have any hibernation or suspension. I didn't change any settings. So, if default setting has them on, then I have them on.

Thanks for the reply.

---

### Post by OldTimeTech on 2007-11-06
Check your power management:

System->Preferences->Power Management

---

### Post by higuava on 2007-11-06
My settings are:
Put computer to sleep when inactive for: never
Put display to sleep when inactive for: 40 minutes
When the power button is pressed: ask me
When the suspend button is pressed: Hibernate
Never display an icon
User sound to notify in an event of error, checked

It is not clear to me if it is caused by power management.
Is there a log that I can check after this happens?
Thanks,

---

### Post by higuava on 2007-11-07
This problem happens every time I leave the computer idle for a while. I just tried to open firefox. I use Ctrl-Alt-F1 to switch to a terminal, type "ps ax" and I can see 3 firefox related processes.
Can somebody help? Should I look for help in a different forum?
Thanks.

---

### Post by llamakc on 2007-11-07
Post the system specs of your computer please.

---

### Post by higuava on 2007-11-07
Hardware?
Emachines T5062
Athlon 64 3800+
integrated NVIDA GeForce 6150SE
1024 MB DDR2
WD 160 GB SATA Harddrive
Seagate freeAgent USB 500 external harddrive, Ubuntu is installed on its first partition.

> **llamakc said:**
> Post the system specs of your computer please.

---

### Post by higuava on 2007-11-09
I may have fixed the problem. After I read this thread:
[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)
I realized that I may have a similar problem: xserver doesn't work properly due to video driver. So I checked my settings and found out that the nVidia driver wasn't enabled in the Restricted Drivers Manager. After I enabled it, I haven't seen that problem in about 24 hours.

---

