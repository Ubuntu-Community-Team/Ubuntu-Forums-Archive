---
title: "Intel 82810E DC-133 Graphics problem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by mrweekender on 2007-06-22
Got a friends mini PC - trying to convert them to Ubuntu.

Only able to get 640x480 resolution on it!? Will not recognize the chip through 915resolution 

xorg.conf using "vesa" instead of "intel" or "i810" crashes if use either of these?

Any ideas folks as this has got me stumped - would dearly love to kill another Windows box :D

---

### Post by overdrank on 2007-06-22
> **mrweekender said:**
> Got a friends mini PC - trying to convert them to Ubuntu.

Only able to get 640x480 resolution on it!? Will not recognize the chip through 915resolution 

xorg.conf using "vesa" instead of "intel" or "i810" crashes if use either of these?

Any ideas folks as this has got me stumped - would dearly love to kill another Windows box :D

Hi, I assume you are using feisty, have you tried ctrl,alt,F1 keys at the same time and enter terminal and login then enter the command  sudo dpkg-reconfigure -phigh xserver-xorg  to see if that helps. :KS

---

### Post by mrweekender on 2007-06-25
Thank you - thats allowed me to boost the res to 1024x786 

Much appreciated 

One less of them - one more of us ;)

---

