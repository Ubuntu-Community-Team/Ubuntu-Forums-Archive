---
title: "Desktop Gnome stting error..will not shutdow and start up is painful."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-12
This is not a double post, I mistakenly posted it in the wrong forum and asked for it to be removed




Ever since installing Feisty 7.04 I have not been able to shutdown other than powering off, I tried sudo shutdown 0 and received a cpu frequency scaling is not supported.

This has never been a problem but now, start up takes forever, I get the login in screen and password quick but it hangs from there.

After 4-5 minutes, I get a Gnome setting daemon error.
I have tried reinstalling the sessions manager and gdm and other Gnome apps but does not change anything. When I run this in terminal this is my outcome.

gnome-settings-daemon
You can only run one xsettings manager at a time; exiting

So I am thinking, maybe KDE would be a better environment? If so how do I choose where to have the desktop environment? I do not have Beryl.

Also how can you kill desktop effects from terminal, from the system menu, there is never an option to disable, only enable and my screen goes haywire so I don't want to mess with desktop effects,

---

### Post by yogo on 2007-08-12
No one has any ideas?

---

### Post by Jeremy23 on 2007-08-12
Try creating a new user, and logging in with him. See if it's any faster. If so, it's your user profile that's the problem, and clearing out your old *.gconf* folder may help a bit (although you'll lose a lot of settings in the process; you can always just try clearing out *.gconf/apps/panel*, which helped me a lot).

---

### Post by yogo on 2007-08-13
Thanks Jeremy, I will give those a try, I installed XFCE4 desktop and that worked out well. I have not shut it down yet to see if it shuts down completely or if I have to do it manually.

It does help with the login, no hang. The Network item does not work for me in XFCE4 and the applet is gone as I thought I may have to configure wireless, but it is connected..I am sure the applet is somewhere, I just have to find it

---

