---
title: "nm-applet 0.6.5"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-03-14
how do i get the nm applet back, i cant find it in my "add to panel" menu, there is just the network monitor which cannot configure youre wireless connection!!!

---

### Post by wormser on 2008-03-14
This is my generic response to this which I just copy and paste.

You need to add the notification area. Right click on the panel> Add to panel. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

---

