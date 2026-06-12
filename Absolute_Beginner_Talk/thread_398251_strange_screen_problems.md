---
title: "strange screen problems"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-31
hey everybody! every since i installed ubuntu after my pc monitor kicks into power save mode and if i wake it up everything is all shakey and such and makes a strange buzzing sound, after about 2 minute's the screen returns to normal again. i do have the latest driver for my video card and it only messes up after i wake the monitor up after it's in power saving mode. this hasnt happened in windows and happened in ubuntu since i installed. is there some way to fix it or a way to turn off power save mode on my monitor?  i tried power management listed under preferences but didnt have monitor settings.

---

### Post by Kobalt on 2007-04-01
Could you please post the output of the following command line, there must be a bad config line in your xerver config file : 
```
cat /etc/X11/xorg.conf
```

---

