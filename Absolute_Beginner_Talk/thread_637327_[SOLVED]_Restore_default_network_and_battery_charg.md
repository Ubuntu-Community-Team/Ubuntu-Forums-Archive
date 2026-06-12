---
title: "[SOLVED] Restore default network and battery charge icons?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-12-10
I accidentally removed the Network and Battery icons that were in the upper toolbar on my desktop.

The network icon shows two monitors on a wired connection, and a series of filled bars on a WiFi connection representing signal strength.  When the icon is left clicked, it shows the available connections and you can choose which one to connect to.  The battery icon shows up when the battery is charging or discharging, and not when I am on A/C power.

I tried to add these back to the panel, specifically the battery charge monitor and network monitor, but they are not the same as the default ones.  I did this by right clicking on the panel and clicking "Add to Panel". Please help me restore the default icons.  Thank you very much for the help.

---

### Post by wormser on 2007-12-10
I have done this before and think this is one thing that needs to become more user friendly.  You need to add Notification Area.  If they still are not appearing then go to System> Preferences> Sessions.  Look for Network Manager and Power Management.  Make sure they are checked.  If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name:  Power Manager
Command:  gnome-power-manager
Comment:  Power management daemon

---

### Post by iamthemicrowave on 2007-12-11
Thank you.  I just needed to add the notification area.  Your response was very complete and helpful!

---

