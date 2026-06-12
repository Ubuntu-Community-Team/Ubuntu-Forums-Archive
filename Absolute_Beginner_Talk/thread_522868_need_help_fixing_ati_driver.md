---
title: "need help fixing ati driver"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by linuxnewbie1113 on 2007-08-11
i was playing around and tried installing flgrx. when i restarted my computer a message pops up that the x-server doesn't work. How can i reset the driver back to the default settings so my graphics load up??

---

### Post by ravenwere on 2007-08-11
From one newb to another, to reset the xorg.conf file in the terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You will then be asked to select your driver,  default is probably vesa and select the screen resolutions your monitor is capable of.

There will probably be a series of backups for xorg.conf that you could compare to see what went wrong.

This command is one of the first learnt by most linux users.;)

All the best

---

### Post by linuxnewbie1113 on 2007-08-11
thanks alot im always runnin into that problem and this definently fixed it.

---

