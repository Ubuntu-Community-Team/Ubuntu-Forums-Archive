---
title: "system hangs up while loading Metacity window manager"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by bars123 on 2006-12-01
Hi,

I am using Ubuntu Edgy Eft. My system is hanging up while **Metacity window manager** is loading. I am logging in using Failsafe Gnome mode. 

While the failsafe mode loads, i get the following message.

[I]There was an error starting the GNOME Settings Daemon.Some things, such as themes, sounds, or background settings may not work correctly.

[B]The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
[/B]
GNOME will still try to restart the Settings Daemon next time you log in.
[/I]

I checked the system log. I found a **critical error message** for the **gnome-power-manager** saying that  the power manager is inactive and it needs dbus to be activated and it should have been the case when gnome starts up

I feel that there is a problem with dbus (no idea what it is !!). Also, in the system monitor, i found that almost all processes are in sleep mode.

The last time I could log in properly, I did an **Ctrl+Alt+Backspace while running beryl**. From then on, I could not log in using **default gnome session**.

Does this have anything to do with the current problem?? please help.

---

### Post by apjone on 2006-12-01
Try creating a new user and login is normally as them, it may be something in your gnome settings in Home dir that it dosen't like

---

### Post by bars123 on 2006-12-04
Thanks a lot. that worked!!! :) :) 

However, i have a doubt: Is there any way that i can use the themes( metacity,icons,etc) that i used in my initial user account?? :-k

---

