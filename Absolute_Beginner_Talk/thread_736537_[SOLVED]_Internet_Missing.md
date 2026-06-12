---
title: "[SOLVED] Internet Missing"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-26
The icon in my upper task bar that let me chose between wireless or cat5 connection for the internet is missing. How can i get it back so I can get back online on my laptop again??

---

### Post by wormser on 2008-03-26
You need to add the notification area too.  Right click on the Panel> Add to Panel> add Notification Area. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

---

### Post by N1N31NCHN41L5 on 2008-03-26
> **wormser said:**
> You need to add the notification area too.  Right click on the Panel> Add to Panel> add Notification Area. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

thats what i was looking for was the notification area. I'm back up again - thanx

---

