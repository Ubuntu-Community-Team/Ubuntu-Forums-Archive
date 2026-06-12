---
title: "[SOLVED] I can't edit Startup Programs."
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Masoris on 2007-03-26
I installed beryl, and I wanted to add "beryl-manager" when startup.

So I opened, System - Preference - Sessions - Startup Programs, and Clicked Add, and typed "beryl-manager", and OK. Then I could see "beryl-manager" in list.
But, when I restart x-window, beryl-manager doesn't start on startup.
So I reopen Sessions, and Startup Programs tab, And I saw that there are no "beryl-manager" in list.

And I tried again it, but it didn't work. Does anybody know about this problem or how to edit it manually?

---

### Post by coxy on 2007-03-26
I'm not 100% sure but have you tried restarting your machine rather than just restarting x? You can also specify when users login if they use the last session, a default session etc. I'm Kubuntu user so not to sure where you could check those settings in Gnome.

---

### Post by Masoris on 2007-03-26
There are error messages in terminal. When I add startup program.
```
user@user-desktop:~$ gnome-session-properties

** (gnome-session-properties:6950): WARNING **: Could not save /home/user/.config/autostart/beryl-manager.desktop file


** (gnome-session-properties:6950): WARNING **: Could not save /etc/xdg/autostart/update-notifier.desktop file


** (gnome-session-properties:6950): WARNING **: Could not save /etc/xdg/autostart/evolution-alarm-notify.desktop file


** (gnome-session-properties:6950): WARNING **: Could not save /usr/share/gnome/autostart/gnome-power-manager.desktop file


** (gnome-session-properties:6950): WARNING **: Could not save /etc/xdg/autostart/gnome-volume-manager.desktop file


** (gnome-session-properties:6950): WARNING **: Could not save /home/user/.config/autostart/beagled.desktop file


** (gnome-session-properties:6950): WARNING **: Could not save /usr/share/gnome/autostart/nm-applet.desktop file

```

---

### Post by eljalill on 2007-03-26
You can put it in ~.config/autostart.
I think it has to be a .desktop for that though,
but you can just copy a .desktop and change the "exec" line into the path to the beryl-manager (executable file)

---

### Post by Masoris on 2007-03-26
> **eljalill said:**
> You can put it in ~.config/autostart.
I think you it has to be a .desktop for that though,
but you can just copy a .desktop and change the "exec" line into the path to the beryl-manager (executable file)

I found the reason.
Because I didn't have permission to edit "~.config/autostart" directory(I don't know why I didn't have permission).

Thank you :)

---

