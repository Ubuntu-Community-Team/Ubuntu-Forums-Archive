---
title: "wirelss meter on panels dissappeared?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by jdehaanjr on 2008-04-13
so this may sound dumb, but the little wireless meter on my panel accidentally got removed?  and I am not sure how to get it back?

can someone help please?  thanks--oh and its not in the add to panel menu.

thanks

---

### Post by wormser on 2008-04-13
I have done this before and think this is one thing that needs to become more user friendly. You need to add Notification Area. Right click on your panel> Add to Panel. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

This is my generic cut an paste response. A lot of problems can be resolved by searching the forum. Don't forget to mark it Solved and give thanks with the little star.

---

