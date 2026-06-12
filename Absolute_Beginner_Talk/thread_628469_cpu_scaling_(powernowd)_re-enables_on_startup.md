---
title: "cpu scaling (powernowd) re-enables on startup"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2007-12-01
I want to turn off cpu scaling in ubuntu gutsy.

I've disabled powernowd in the Services but, everytime I reboot, it is scaling my cpu, again. I know this, because the Cpu scaling monitor on my panel shows that it's changing. So, everytime I reboot, I have to open Services, and check-&-uncheck powernowd to turn it off. I've also run these two commands:
```
sudo /etc/init.d/powernowd stop
sudo update-rc.d -f powernowd remove
```
but, still the same.

Any suggestions?

Oh, and if you're wondering why I'm disabling it, it's because my system freezes, usually when using Firefox, and turning it off seems to fix the problem. It's an issue with the nVidia drivers.

---

