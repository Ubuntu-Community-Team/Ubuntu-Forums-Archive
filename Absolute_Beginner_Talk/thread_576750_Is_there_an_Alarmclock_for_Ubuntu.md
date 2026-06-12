---
title: "Is there an Alarmclock for Ubuntu?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by _d5 on 2007-10-15
Is there an Alarmclock for Ubuntu?

Thank you!

---

### Post by LowSky on 2007-10-15
there is an alarm clock plugin for exhaile... amarok might have one too... check synaptic there might be one floating around in the repositories

---

### Post by rsambuca on 2007-10-15
Try wmclockmon from the repositories.  You can install it using the Synaptic Package Manager.  Go to your top menu bar and select "System -> Administration -> Synaptic Package Manager"

Just select wmclockmon for installation and the select "Apply".

---

### Post by _d5 on 2007-10-15
I have installed it, i logged out and entered, but i still can not find the application anywhere

---

### Post by buntunub on 2007-10-15
Its probably a panel applet.

---

### Post by jordanmthomas on 2007-10-15
If all else fails, cron + mplayer will work.

---

### Post by rsambuca on 2007-10-15
You can start it in a terminal by typing ```
wmclockmon
```, and you can see the manual first if you want by typing ```
man wmclockmon
```I have just tried it for you, and to be honest it works, but it isn't really pretty!

---

### Post by wolfen69 on 2007-10-15
kalarm is in synaptic.

---

### Post by _d5 on 2007-10-16
> **jordanmthomas said:**
> If all else fails, cron + mplayer will work.

How could I create a Cron Job for mplayer????

---

### Post by Sim777 on 2007-10-23
Is there anything else? On windows I used [http://www.download.com/Alarm-Clock/3000-2350_4-10064069.html?pid=7087271](http://www.download.com/Alarm-Clock/3000-2350_4-10064069.html?pid=7087271) which is a great little tool at only 1mb size. 

For K-Alarm it asks to Dled 54mb...and wmclockmon is not working right. 

(on Gutsy w/Compiz)

---

### Post by rsambuca on 2007-10-23
I found a couple more alarm clocks in the repositories for you to try:

dclock
sanduhr

---

### Post by jordanmthomas on 2007-10-23
It looks like the link you posted works in wine (for me anyway).

---

### Post by Sim777 on 2007-10-23
I feel like a guinea-pig... 

will be back after testing...

---

### Post by Sim777 on 2007-10-23
> **jordanmthomas said:**
> It looks like the link you posted works in wine (for me anyway).

Is there a way to run it natively?

---

### Post by rsambuca on 2007-10-23
Sorry Sim, I didn't think of this earlier because I never use it, but Evolution (the default email and calendar program) has alarm functions.  Just click on your clock on the taskbar, and it will open a calendar.  Click on the day you want to set the alarm(s) for, and you will open the appointment calendar where you can set alarms, etc.

---

### Post by jordanmthomas on 2007-10-23
> **Sim777 said:**
> Is there a way to run it natively?
Not without recompiling it from source.  Wine does run things natively though (**W**ine **i**s **n**ot an **e**mulator)

---

