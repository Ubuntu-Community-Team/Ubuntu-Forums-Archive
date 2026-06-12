---
title: "Removed Network From Panel"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-21
I accidently deleted the Network Wireless Icon from my panel and now I can't connect to the internet! How do I re-add it to my panel and gain back my ability to connect to the internet!??

---

### Post by wormser on 2007-12-21
I have done this before and think this is one thing that needs to become more user friendly. You need to add Notification Area. Right click on your panel> Add to Panel. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

---

### Post by jordank on 2007-12-21
It says they are both checked however, the icon is not there. You know which icon I am talking about right? When I typed in the Network command line, I got Command Not found.

---

### Post by wormser on 2007-12-21
I know what icon you are talking about.  The one near the clock.  Did you add the Notification Area?  Try this command then reboot.

```
nm-applet --sm-disable
```

---

### Post by jordank on 2007-12-21
Ahhh! Thank you. Found network notificiation area. Merry Christmas.

---

### Post by wormser on 2007-12-21
> **jordank said:**
> Ahhh! Thank you. Found network notificiation area. Merry Christmas.

No problem and Happy [Festivus]("http://www.whatisfestivus.com/").  Make sure you mark this thread as Solved.

---

