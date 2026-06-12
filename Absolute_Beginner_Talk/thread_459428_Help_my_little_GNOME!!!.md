---
title: "Help my little GNOME!!!"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by bgissal on 2007-05-30
I was tinkering around in the Sessions applet today and think I made a mistake. I tried to get the command, "sudo iwconfig wlan0 assid asdf", to run at startup so my Dell c400 laptop w/ 7.04 & GNOME could connect to the wireless internet. 

But somehow I think I made things worse. When I reboot my computer it takes a good 1-2 minutes for Beryl and Network Manager to load. Also, it takes 1-2 minutes after I click the door with the arrow to load the interface "log off, switch user, lock screen or power down the computer."

I booted up in failsafe GNOME and this delay doesn't happen. Everything is loaded right away. Is there any way to get the GNOME to run like the failsafe? Can this problem be fixed by changing something in sessions??????

---

### Post by GrueTamer on 2007-05-30
Failsafe gnome is gnome without any startup tasks, so I would bet that it's one of your startup tasks doing this.  But I am sorry, I do not remember off hand what file controls these, but I shall try and find out, if someone doesn't beat me to it.

---

