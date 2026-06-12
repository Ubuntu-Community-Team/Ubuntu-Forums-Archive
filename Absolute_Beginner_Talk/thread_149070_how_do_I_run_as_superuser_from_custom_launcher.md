---
title: "how do I run as superuser from custom launcher?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by jjf on 2006-03-23
I got wifi-radar and added a "Custom Application Launcher" to my gnome panel.  wifi-radar needs to be run as superuser, so I put the command in as ```
sudo wifi-radar
```

It doesn't do anything, I imagine because somewhere in the process it's waiting for the password.  The same command runs fine from the terminal (after prompting for my password), so my question is how do I add my password to the launcher so I can just click the icon to run wifi-radar.  Thanks.

---

### Post by dermotti on 2006-03-23
gksudo wifi-radar

---

### Post by jjf on 2006-03-23
thanks!

---

