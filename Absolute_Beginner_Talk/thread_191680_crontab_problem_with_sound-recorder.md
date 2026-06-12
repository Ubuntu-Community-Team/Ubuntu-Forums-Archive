---
title: "crontab problem with sound-recorder"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-06-07
If I set up crontab like this: 
     02 20 * * 3 sound-recorder -c 1 -S 40:00 -f wav opera.wav
it works. 

If I set up crontab like this: 

   02 20 * * 3 sound-recorder -c 1 -S 240:00 -f wav opera.wav
it never starts. 

-S 240 minutes is a valid parameter for sound-recorder and works just fine from the command line. Why not from cron?

PS: Ubuntu 5.10, gnome clearview desktop.

---

### Post by falcon15500 on 2006-06-22
Am not sure why it doesn't start.  Have you checked your syslog?

falc

---

