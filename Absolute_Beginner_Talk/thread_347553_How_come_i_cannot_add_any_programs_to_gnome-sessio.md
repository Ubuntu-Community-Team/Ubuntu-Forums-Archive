---
title: "How come i cannot add any programs to gnome-session?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by davidY on 2007-01-27
Hi, I am trying to add a program to gnome-session to start up - in the system -> preferences -> session. HOwever, when I add it, and then i relode the program, it shows that I never added that program. I have tried this several times, and it never saves the thing. I loaded it in a terminal and the output was: 

```
** (gnome-session-properties:16839): WARNING **: Could not save /home/nmenon/.config/autostart/beryl-manager.desktop file


** (gnome-session-properties:16839): WARNING **: Could not save /etc/xdg/autostart/update-notifier.desktop file


** (gnome-session-properties:16839): WARNING **: Could not save /etc/xdg/autostart/evolution-alarm-notify.desktop file


** (gnome-session-properties:16839): WARNING **: Could not save /etc/xdg/autostart/gnome-power-manager.desktop file


** (gnome-session-properties:16839): WARNING **: Could not save /etc/xdg/autostart/gnome-volume-manager.desktop file


** (gnome-session-properties:16839): WARNING **: Could not save /home/nmenon/.config/autostart/beagled.desktop file

```

---

### Post by aidanr on 2007-01-27
try

sudo chown -R nmenon /home/nmenon/.config
sudo chgrg -R nmenon /home/nmenon/.config
sudo chmod -R 755 /home/nmenon/.config

---

