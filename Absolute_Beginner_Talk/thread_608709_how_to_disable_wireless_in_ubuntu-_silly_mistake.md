---
title: "how to disable wireless in ubuntu- silly mistake"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by mhedges48 on 2007-11-10
In order to easily disable wireless in Ubuntu, be sure you have not removed the systray ("Notification Area") from a panel or AWN. I had removed the systray and spent a few hours trying to figure out how to switch off wireless using the network monitor, which doesn't have that option... what does is nm-applet which as far as I know requires the systray... hope my silly mistake saves someone some hours...

Matt

---

### Post by Nano Geek on 2007-11-10
For those who are interested, you can also do it by running:```
sudo /etc/init.d/networking stop 
```

---

