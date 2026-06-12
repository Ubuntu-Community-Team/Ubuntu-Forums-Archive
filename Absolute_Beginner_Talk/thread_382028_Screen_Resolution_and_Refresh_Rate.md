---
title: "Screen Resolution and Refresh Rate"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by offramp13 on 2007-03-11
When I am in 1024 X 768 resolution my refresh rate can be 85. But, when i go into 1280 X 1024, my refresh rate drops down to 60, and i cant change it. Is there any way i can force the refresh rate to stay at 85, even at 1280 X 1024.

---

### Post by ljpm on 2007-03-11
Make sure you have the correct hscan and vscan values for your monitor in our xorg.conf file. Correcting this and reconfiguring xserver-xorg may allow you to set the higher refresh rate.

---

### Post by oilchangeguy on 2007-03-11
read this, [http://www.ubuntuforums.org/showthread.php?t=381157](http://www.ubuntuforums.org/showthread.php?t=381157)

---

