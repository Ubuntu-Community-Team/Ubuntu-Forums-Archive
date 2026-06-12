---
title: "Time"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-05-19
Hello!
I have a problem with setting the correct date and time on my computer.
I have Ubuntu dual booting with Windows Xp Pro.

When booting, syncronizing to ubuntu's timeserver fails _always_. When I boot up, the time is incorrect. So I set it to the correct time. Everything seems to be fine, until I boot up Windows. Now, the time in windows is incorrect! So I set the correct time, boot Ubuntu, but uh-oh... incorrect time here! ](*,) 

It seems like these 2 OSes interact with each other, and when I set the time on one, the other somehow sets its time to incorrect one.

What's the problem? Am I doing something wrong?

---

### Post by jasay on 2006-05-19
Linux and Windows both check to see what time it is and reset the hardware clock.  The problem is that windows sets the clock to local time and linux sets it to UTC, so if you change from one to the other it will off by +/- your timezone.  To fix this 
```
gksudo gedit /etc/default/rcS
```and change the yes in this line to no```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
```

---

### Post by Klaidas on 2006-05-19
Thank you - I have just edited the file. I'll inform if it won't work, but I guess it will :)
Thank you very much, 
Klaidas

---

### Post by jorn on 2006-05-19
Maybe you know this guide. 
[http://makuchaku.info/amnesty/#disablesystemtimedateutc](http://makuchaku.info/amnesty/#disablesystemtimedateutc)

---

