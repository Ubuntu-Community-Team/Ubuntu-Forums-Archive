---
title: "Systme Clock (Time) Change"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Zero7 on 2008-01-11
I dual boot Windows XP and Gutsy Gibbon. I have to problems. I am not sure if they are related to each other.

1) Whenever I boot Ubuntu and go back to windows system time gets reset to GMT. In Ubuntu I have set the location correctly. This problem does not occur if I use only windows xp. Only when I boot linux I get this problem.

2) If I boot in to Ubuntu and shutdown, after restart, system power and HDD LEDs turn on, but no boot up screen and monitor is blank. I do not hear system beep also. I have to switch of power supply and turn it on 3 to 4 times to get the system boot.

Hardware

---

### Post by yabbadabbadont on 2008-01-11
1) One of the files in /etc/default (clock maybe?) is where you specify whether or not Ubuntu stores the time in UTC or local.  You need to make sure that it is set to local.

---

