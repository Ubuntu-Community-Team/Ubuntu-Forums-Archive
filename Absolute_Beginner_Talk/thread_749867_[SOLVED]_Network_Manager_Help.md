---
title: "[SOLVED] Network Manager Help"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by tiggnet on 2008-04-08
Hello,

I accidentally deleted the Network Manger entry in the start up sessions.  Now everytime I reboot, I cannot get into the internet.  

How can I add back the Network Manager in the start up?

Thanks.

---

### Post by tiggnet on 2008-04-08
SOLVED:

I put the command line:

nm-applet --sm-disable


reboot and I was back on my wireless

---

### Post by Slushdoot on 2008-04-08
Add a startup entry that points to /usr/bin/nm-applet some time early in the order. :)

---

### Post by wormser on 2008-04-08
I have done this before and think this is one thing that needs to become more user friendly. You need to add Notification Area. Right click on your panel> Add to Panel. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

This is my generic cut an paste response.  A lot of problems can be resolved by searching the forum.  Don't forget to mark it Solved and give thanks with the little star.

---

