---
title: "[SOLVED] Lost Panel Icons - how to fix?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by wolf3491 on 2008-03-13
Ubuntu is on my laptop, and I accidentally removed the nm-applet icon and battery charge icon from the panel.  How can I put them back on, they make things very convenient for me.  I tried starting nm-applet again, but the icon doesnt show up on the top panel like it used to. Also, the battery manager icon, what is the process name for it?  Thanks. :)

---

### Post by bumanie on 2008-03-13
Right click on the panel and left click on Add to panel. There are a number of applets you can choose from.

---

### Post by linux phreak on 2008-03-13
You can put them back using the add to panel option.Right click on the panel and select the required programs to add.

---

### Post by wormser on 2008-03-14
You might need to add the notification area too.  I have done this before and think this is one thing that needs to become more user friendly. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

---

