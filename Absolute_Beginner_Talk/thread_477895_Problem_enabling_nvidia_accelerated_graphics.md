---
title: "Problem enabling nvidia accelerated graphics"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Rich1386 on 2007-06-18
I enabled the accelerated driver in the Restricted Drivers window and restarted the computer, and it boots to a screen saying this 

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

Unfortunately, I didn't make any backups before enabling the accelerated driver.

---

### Post by skymera on 2007-06-18
reconfigure X and start again

```
 sudo dpkg-reconfigure xserver-xorg 
```

also check 
[www.ubuntuguide.org](www.ubuntuguide.org)
for how to install nVIDIA graphics :)

---

### Post by Rich1386 on 2007-06-18
I went through all the questions it asked, and then rebooted the computer, but it just brought me to the same screen.

---

