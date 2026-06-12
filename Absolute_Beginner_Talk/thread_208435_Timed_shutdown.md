---
title: "Timed shutdown"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-03
How can i make a timed shutdown?

---

### Post by shanepardue on 2006-07-03
To shut down the system at a certain time, give that time (in 24-hour format) as an argument. 

To shut down and then reboot the system at 4:23 a.m., type: 
sudo shutdown -r 4:23 [RET]

To shut down and halt the system at 8:00 p.m., type: 
sudo shutdown -h 20:00 [RET]

To shut down the system in a certain number of minutes, give that number of minutes prefaced by a plus sign (`+'). 

To shut down and halt the system in five mintues, type: 
sudo shutdown -h +5 [RET]

---

### Post by blanc11 on 2006-07-03
Can you undo something like this?

---

### Post by byen on 2006-07-03
Yes blanc11, shanepardue has explained it well on his post. All you have to do is use the following in the terminal:

sudo shutdown -h +x
where x can be replaced by the number or minutes such as 
sudo shutdown -h +30
sudo shutdown -h +90

or at a specific time such as 
sudo shutdown -h time

where "time" is replaced by the actual time in a 24 hr format...for eg.
sudo shutdown -h 21:00

I use it everynight so that the music/pc turns off after i fall asleep. So go ahead and try it out. Goodluck!

---

### Post by blanc11 on 2006-07-03
But is there a way to turn off the automatic shut off?

---

### Post by bollix47 on 2006-07-03
You can end the shutdown process in system monitor under processes.

---

### Post by byen on 2006-07-03
[QUOTE=blanc11]But is there a way to turn off the automatic shut off?[/QUOTE]

Simple, just type the following command in the terminal to stop this timed shutoff
```
sudo shutdown -c
```

Hope that helps!

---

