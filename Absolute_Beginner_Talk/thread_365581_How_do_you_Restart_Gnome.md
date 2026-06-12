---
title: "How do you Restart Gnome"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-02-19
Hi.  Recently I've had a couple of minor quirks with gnome.  After a program crash, my desktop icons will no longer show on the desktop and nautilus won't work.  I can get to a terminal with ctrl+alt+f1.  From there, what is the command to restart my session of Gnome?

---

### Post by meng on 2007-02-19
GNOME is still running if you switch to ctrl-alt-f1, you can confirm this by pressing ctrl-alt-f7 and ending up where you started. If you want to stop and then restart GNOME, try ctrl-alt-bksp.

---

### Post by l951b951 on 2007-02-19
ctrl+alt+backspace doesn't respond for me, so I was looking for a direct command line to kill it and then re-enable it.

---

### Post by r4ik on 2007-02-19
sudo /etc/init.d/gdm restart

---

